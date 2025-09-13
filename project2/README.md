# Dockerizing an Apache Web Server

## steps

```yaml
docker build -t my-apache-image .
docker run -d --name my-apache-container -p 8080:80 my-apache-image

```
- Verify Apache is Running.
`http://localhost:8080`

## resources
https://www.docker.com/blog/how-to-use-the-apache-httpd-docker-official-image/
