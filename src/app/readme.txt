steps:

1. ng new my-docker-app
2. cd my-docker-app
3. Dockerfile maken:

FROM johnpapa/angular-cli
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app/
RUN ["npm", "install"]
COPY . /app
EXPOSE 4200/tcp
CMD ["npm", "start", "--", "--host", "0.0.0.0", "--poll", "500"]

in powershell (belangrijk voor ${pwd}, betekent huidige directory, weet niet wat syntax in cmd):
4. Docker build -t my-docker-app .

5. docker run -it -d -p 4000:4200 -v ${pwd}/src:/app/src --name my-docker-app my-docker-app