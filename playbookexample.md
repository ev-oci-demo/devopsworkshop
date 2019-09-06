<b>A very simple playbook</b>
For our first example playbook, we’ll configure a host to run an Nginx web server.

- name: Configure webserver with nginx
  hosts: webservers
  become: True
  tasks:
    - name: install nginx
      apt: name=nginx update_cache=yes

    - name: copy nginx config file
      copy: src=files/nginx.conf dest=/etc/nginx/sites-available/default

    - name: enable configuration
      file: >
        dest=/etc/nginx/sites-enabled/default
        src=/etc/nginx/sites-available/default
        state=link

    - name: copy index.html
      template: src=templates/index.html.j2 dest=/usr/share/nginx/html/index.html
        mode=0644

    - name: restart nginx
      service: name=nginx state=restarted
      
 This playbook requires two additional files before we can run it. First, we need to define an Nginx configuration file.

Nginx ships with a configuration file that works out of the box if you just want to serve static files. But you’ll almost always need to customize this, so we’ll overwrite the default configuration file with our own as part of this playbook. Put it in playbooks/files/nginx.conf.

server {
        listen 80 default_server;
        listen [::]:80 default_server ipv6only=on;

        root /usr/share/nginx/html;
        index index.html index.htm;

        server_name localhost;

        location / {
                try_files $uri $uri/ =404;
        }
}

Let’s add a custom home page. We’re going to use Ansible’s template functionality so that Ansible will generate the file from a template. Put the content in playbooks/templates/index.html.j2

<html>
  <head>
    <title>Welcome to ansible</title>
  </head>
  <body>
  <h1>nginx, configured by Ansible</h1>
  <p>If you can see this, Ansible successfully installed nginx.</p>

  <p>Running on {{ inventory_hostname }}</p>
  </body>
</html>
