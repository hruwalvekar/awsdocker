# 4-Hour Practical Workshop Guide

## 1. Embedded Systems Simulation
- Simulate sensor data using Python on Ubuntu.
- Example: `sensor_simulator.py` generates random temperature and humidity readings.
- Logs data to a file every 2 seconds.

```bash
python3 sensor_simulator.py
```

## 2. AWS EC2 & S3 Cloud Concepts
- Create AWS Free Tier account.
- Launch Ubuntu EC2 (t2.micro), open ports 22 and 80.
- SSH into EC2 and install Apache to host a simple web page.

```bash
ssh -i key.pem ubuntu@your-ec2-ip
sudo apt install apache2
```

- Upload files to S3:

```bash
aws s3 cp file.txt s3://your-bucket-name/
```

## 3. Git & GitHub Version Control
- Configure Git and create local/remote repo.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git init
```

- Push code and handle merge conflicts with branches.

```bash
git add . && git commit -m "Initial commit"
git push -u origin master
```

## 4. Docker & CI/CD Workflow
- Create and containerize a simple Flask app.

**Dockerfile**
```Dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install flask
CMD ["python", "app.py"]
```

- Build and run locally, push to Docker Hub.

```bash
docker build -t embedded-app .
docker run -p 5000:5000 embedded-app
docker tag embedded-app yourusername/embedded-app
docker push yourusername/embedded-app
```

- GitHub Actions CI:

```yaml
name: Docker CI
on:
  push:
    branches: [ "main" ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Build Docker Image
        run: docker build -t embedded-app .
```

## 5. Edge-to-Cloud Integration Project
- Host a Flask API on EC2 to receive sensor data via POST.
- Send data from local script to the cloud.

```python
requests.post("http://<ec2-ip>:5000/data", json=data)
```

- Optional: Display data on a web dashboard (HTML, Chart.js).

## 6. Wrap-Up and Submission
**Deliverables:**
- GitHub repo with source code and Dockerfile
- Docker Hub image
- Screenshot of EC2 app running
- CI badge (optional)

**Resources:**
- [Flask Docs](https://flask.palletsprojects.com/)
- [Docker Playground](https://labs.play-with-docker.com/)
- [AWS Educate](https://aws.amazon.com/education/awseducate/)
- [GitHub Docs](https://docs.github.com/)
