# nginxdockerimage
    2  docker version
    3  sudo systemctl status docker
    4  git -version
    5  git version
    6  sudo apt -update
    7  sudo apt update
    8  sudo apt -get install nginx
    9  sudo apt-get install nginx
   10  ls -lstr
   11  sudo systemctl status nginx
   36  sudo vi /etc/nginx/sites-enabled/default
  -- port changed 80 to 8081
   37  sudo systemctl restart nginx
   38  sudo systemctl status nginx
   39  sudo nginx -t
   40  sudo service nginx reload
   41  sudo systemctl status nginx
   42  mkdir dockerproj1
   43  ls -l
   44  cd dockerproj1
   47  vi index.html
   {
   <html>
<body>
<h1>Welcome to nginx docker!</h1>
</body>
</html>
}
48  vi nginx.conf
 
 {
 server {
  listen       80 default_server;
  listen       [::]:80 default_server;

  server_name  _;
  root         /usr/share/nginx/html;

  location / {
  }
}
 
 }
 49  vi dockerfile
   {
   FROM nginx:latest
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY index.html /usr/share/nginx/html
}
   51  docker build -t nginximage .
   52  docker images
   55  docker run --name my-nginx-container1 -d -p 8080:80 nginximage
   56  docker container
   57  docker container ps -a
   58  docker login ghcr.io -u GITHUB_USERNAME
   

   61  docker tag IMAGE_NAME:VERSION ghcr.io/sindhu-kotha/nginximage:latest
   62  docker tag nginximage:latest ghcr.io/sindhu-kotha/nginximage:latest
   63  docker push ghcr.io/sindhu-kotha/nginximage:latest
   
   
