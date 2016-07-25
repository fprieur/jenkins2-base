#### Builder le projet
<pre>docker build -t jenkins2 .</pre>

#### Rouler l'application
<pre>docker run -d -p 8081:8080 -p 50001:50000 -v /tmp/jenkins2:/var/jenkins_home -u jenkins jenkins2</pre>

#### Dans un premier temps, il faut récupérer le crum
<pre>CRUMB=$(curl -s 'http://admin:e76cff3fb7d552e82a8a0b223d2934f5@localhost:8081/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)')</pre>

###### Finalement, on peut créé des pipeline si un fichier Jenkinsfile existe dans le dépot git de l'url spécifier dans le fichier de config
<pre>curl -X POST -d @henrimulti3.txt -H $CRUMB "http://admin:e76cff3fb7d552e82a8a0b223d2934f5@localhost:8081/createItem?name=multihenri3" --header "Content-Type:text/xml"</pre>
