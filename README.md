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
3) Change port number from 22 to 2200 by executing the file: <code> sudo vim /etc/ssh/sshd_config </code> and modifying line 5: <code> Port 2200 </code> to <code> Port 22 </code>
4) Execute the following commands for the firewall settings:
<ul>
  <li></li>
</ul>
