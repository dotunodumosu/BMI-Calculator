How to run a local test web server.

Once you get the server running, go to the ip address /index.html  eg: http://192.168.0.6

### Install the http-server package from npm
## Install the http-server globally on your machine using the node package manager (npm) command line tool, this will allow you to run a web server from anywhere on your computer.

Open a command prompt / command line window and enter the following:
```
npm install -g http-server
```
Start a web server from a directory containing static website files
Change to the directory containing your static web files (e.g. html, javascript, css etc) in the command line window, e.g:
```
cd \projects\angular-registration-login-example
Start the server with this command:
```
http-server
You should see something like the following:
```
C:\projects\angular-registration-login-example>http-server
Starting up http-server, serving ./
Available on:
  http://192.168.0.5:8080
  http://127.0.0.1:8080
Hit CTRL-C to stop the server
```
Browse to your local website with a browser
Open your browser and go to the address http://localhost:8080 and you should see your local website. 