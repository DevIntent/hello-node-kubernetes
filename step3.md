# 3. Create your Node.js application

Estimated time: 53 min remaining

The first step is to write the application that we want to deploy to Google Container Engine. 
Here is a simple Node.js server:
```
$ nano server.js
```
```javascript
var http = require('http');
var handleRequest = function(request, response) {
  response.writeHead(200);
  response.end("Hello World!");
}
var www = http.createServer(handleRequest);
www.listen(8080);
```
**Note**: We recommend using the nano editor but `vi` and `emacs` are also available in Cloud Shell.

From Cloud Shell simply exit the editor and save the `server.js` file. Since CloudShell has the `node` executable 
installed we can now run this simple command:
```
$ node server.js
```
Then use the built-in [Web preview feature](https://cloud.google.com/cloud-shell/docs/features#web_preview) of CloudShell to open a new browser tab and proxy a request to the 
instance you just started on port 8080.

![web-preview](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-8.png)
![hello-node-preview](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-9.png)

Now, more importantly, let’s package this application in a Docker container.

Before we continue, simply stop the running node server by pressing Ctrl-C in CloudShell.

#### [Go to step 4](step4.md)
#### [Go back to step 2](step2.md)
