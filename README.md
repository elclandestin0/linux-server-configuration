# linux-server-configuration
Hello and welcome to the linux-server-configuration!
<strong> Side note: </strong> only the Udacity team will be able to view my project on the server,
as they are the only ones who will have access to the private key to my Lightsail instance. However,
I will provide screenshots to document the steps required to reproduce this project.

1) Start a new Ubuntu Linux instance on Lightsail. Instructions can be found <a href="https://lightsail.aws.amazon.com/ls/docs/getting-started/article/getting-started-with-amazon-lightsail"> here </a>
2) Follow the instructions required to SSH into that instance. You can do that securely from your browser (via the Lightsail web app), but I highly suggest you do this from your local terminal to get your fingers dirty on working around with ports. To do this: <br>
<ul>
  <li> Download the key from the Lightsail instance home page </li>
  <li> <code>mv</code> the key into the <code>.ssh/</code> directory in your homepage </li>
  <li> Protect the key by executing the command: <code>chmod 600 <i>path-to-key</i> </code> </li>
  <li> SSH using your local terminal by executing the command: <code>ssh -i <i>path-to-key</i> ubuntu@<i>ip-address-here</i> -p <i>2200</i></code></li>
</ul>
3) Update packages by: <code>sudo apt upgrade</code> and <code> sudo apt update</code>
4) Change port number from 22 to 2200 by executing the file: <code> sudo vim /etc/ssh/sshd_config </code> and modifying line 5: <code> Port 22 </code> to <code> Port 2200 </code>
5) Execute the following commands for the <code>ufw</code> settings:
<ul>
  <li><code>sudo ufw default deny incoming connections</code></li>
  <li><code>sudo ufw default allow outgoing connections</code></li>
  <li><code>sudo ufw allow 2200/tcp</code></li>
  <li><code>sudo ufw allow 123/tcp</code></li>
  <li><code>sudo ufw allow 80/tcp</code></li>
  <li><code>sudo ufw enable</code></li>
</ul>
6) Create new user <code>grader</code> by executing the command <code> sudo adduser </code> grader
7) Give <code>grader</code> the permission to <code> sudo </code> by executing the following command: <code> sudo vim /etc/sudoers.d/grader </code> and adding the line <code> grader ALL=(ALL) NOPASSWD:ALL </code>
8) Create a SSH key-pair for grader by doing the following:
- Switch to grader through the remote terminal: <code>su - grader</code>
- <code>mkdir .ssh</code> and <code> touch .ssh/authorized_keys</code>
- <code> ssh-keygen </code> then execute <code>cat <your-keygen-name.pub> </code>, copy the text and paste it in the remote machine's <code>authorized_keys</code>
- <code> ssh </code> into grader as a user using the ip address and the keygen you just generated.
9) Configure the local timezone to UTC by doing the following:
- <code>sudo dpkg-reconfigure tzdata </code>
- Scroll down to select <code> None of the above </code> then selecting <code> UTC </code>

10) Install and configure apache to serve a Python mod_wsgi application. Instructions
followed <a href="https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-apache-and-mod_wsgi-on-ubuntu-16-04">here</a>

11) Install and configure PostgreSQL. Instructions followed here <a href="https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps"> Here </a>

12) Install git by executing <code> sudo apt install git </code>
13) <code> git clone <name-of-repository> </code>
14) Deploy the item catalog <a href="18.219.103.164:8000"> project </a>
