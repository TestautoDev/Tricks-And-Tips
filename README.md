# Tricks-And-Tips

## Jenkins
### To Allow html css in html publisher
Go to jenkins script console and run the below command  
```System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "sandbox allow-same-origin allow-scripts; default-src 'self'; script-src * 'unsafe-eval'; img-src *; style-src * 'unsafe-inline'; font-src *")```
