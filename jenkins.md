# Tricks-And-Tips

## Jenkins
### To Allow html css in html publisher
Go to jenkins script console and run the below command  
```System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "sandbox allow-same-origin allow-scripts; default-src 'self'; script-src * 'unsafe-eval'; img-src *; style-src * 'unsafe-inline'; font-src *")```

### Demo jenkisnfile for multibranch javascript
```
def buildVersion = ''

pipeline {
  agent  { label 'win' }
	triggers { cron('15 09 * * *') }

    parameters {
        string(name: 'exec_config', defaultValue: 'ENV', description: 'Default execution environment is ENV headless')
    }

	options {
			buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
		}

    stages {
	 stage("Test ENV") {
			steps {
				echo 'run tests'
				sh 'npm run test:headless'
				echo "${params.exec_config}"
				sh "npm run test:e2e:${params.exec_config}"
			}
		}

	}
	post {
		always {
              allure includeProperties: false, jdk: '', results: [[path: 'allure-xml-results']]
              publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'allure-report', reportFiles: 'index.html', reportName: 'Allure Report', reportTitles: ''])
		}
	}
```
### EmailableReport
Hi All,
<br/>
Please find the execution detail and buildlog in attachment.
<br/>
Report url: /<br/>
<br/>
<pre>
${FILE, path="build/testngOutput/emailable-report.html"}
</pre>

Attachments: Reports/*.html
