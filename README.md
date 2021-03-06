# Loowid [![Build Status](https://travis-ci.org/loowid/loowid.svg?branch=master)](https://travis-ci.org/loowid/loowid)


*LOOk What I'm Doing* is a web application that allows you to connect with other users and share audio, video, screen and files without any plugin using WebRTC technology.

https://www.loowid.com
  
## Install

  1. You need to install nodejs, mongo and git before run loowid.
  2. Download source code.`
      git clone https://github.com/loowid/loowid /install/dir
`
  3. Create and download public and private keys of your self-signed certificate.
      http://www.cert-depot.com/
  4. `npm install --production`
  5. `npm start`
  6. Connect to https://localhost/

**Note**: If you want to work with the **latest stable release** then you must clone `https://github.com/loowid/loowid/tree/1.1.0`

## Docker

  Too many steps to install? Don't worry loowid is also dockerized !!
  
  https://github.com/loowid/loowid-docker
  
## Development

  Follow the same steps but chage steps 5 and 6:
  
  5. `npm install`
  6. `grunt` (Default development server, "grunt prod" for production environment)
  
	 * `grunt cluster`	: Run default development cluster server with 2 nodes (--nodes=N change default value)
	 * `grunt minijs`	: Minify client js files
	 * `grunt less`		: Compile less sources to css
	 * `grunt mini`		: Minify js files and compile less
	 * `grunt jshint`	: Analyze js files to check style and best practices
	 * `grunt test`		: Run unit tests

	 ```
	 Use --port=80 --sport=443 --bport=8000 to change default port values.
	 ```
	 ```
	 grunt cluster --sport=9090 --port=8080 --bport=7000 --nodes=3 will listen in ports 8080, 7001, 7002, 7003 (http) and 9090 (https).
	 ```
	 ```
	 grunt --port=8080 will listen in ports 443 (https) and 8080 (http).
	 ```
   
  7. If you get some npm packages errors try `npm update` (We had that errors on Windows 7 64bits)
  
## Configuration


  There are some environment variables you may set to configure your loowid deployment. 
  Check your hosting provider documentation in order to know how to set this values, for example, with openshift you can type:
  ```
  	rhc env set VARIABLE=VALUE -a app
  ```
  1. Credentials to access to some admin resources (debug level and stats). By default admin/admin.

  ```
  ADMIN_USERNAME=<your-admin-username>
  ADMIN_PASSWORD=<your-admin-password>
  ```
  2. Chrome plugin extension id. Set the id of your own plugin extension for screen sharing. A generic domain plugin will be used by default.
  
  ```
  CEXTID=<generic-domain-plugin-id>
  ```
  3. Xyrsys configuration, to configure access to xyrsys (https://xirsys.com/).
  
  ```
  XIRSYS_DOMAIN=<xyrsis domain>
  XIRSYS_USER=<xyrsys usename>
  XIRSYS_SECRET=<xyrsys password>
  ```
  4. Room timeout. The number of days that a room can be active on the server before expires (15 days by default).

  ```
  ROOM_TIMEOUT=15
  ```
  5. Path to certificate files. By default `public.pem` and `private.pem` in the same folder, you could set the full path to your own certificate files.

  ```
  PUBLIC_KEY=<path-to-your-cert-public.pem>
  PRIVATE_KEY=<path-to-your-privatekey.pem>
  ```

  6. LTI Producer Configuration. The consumer connects with multiple loowid rooms depends on LTI context, the first user with OWNER_ROLE will be the room owner. 
  The loowid producer entrypoint is configured with LTI_PATH (/lti). Set LTI_DOMAIN if your host is behind a proxy with other domain than req.headers.host. 

  ```
  LTI_KEY=<lti-key>
  LTI_SECRET=<lti-secret>
  LTI_PATH=<lti-url>
  LTI_DOMAIN=<lti-host>
  LTI_OWNER_ROLES=<lti-owner-role1>,<lti-owner-role2>,...
  ```

