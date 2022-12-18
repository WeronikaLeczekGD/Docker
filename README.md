# Docker

1. Fork GitHub - spring-projects/spring-petclinic: A sample Spring-based application

2. [Create Dockerfile for Spring-petclinic application using pre-built artifact](#ad-2)

- Build application outside of container

- Copy artifact from target folder into image and make it work inside container

3. [Create multi-stage Dockerfile for Spring-petclinic application](#ad-3)

- Application should be built as part of first stage

- Final image should contain only required files and based on minimal possible base image

4. [Create docker-compose configuration that will automatically start multiple containers](#ad-4)

- Run two containers: application + DB

- Provide credentials as environment variables, so DB image can be configured with custom credentials and application can connect to DB automatically

## Ad 2

To build application outside of container I used ```gradlew build```

After building application outside of container I copied artifact from target folder into image and made it work inside container. So my Dockerfile looks like this:

My Dockerfile:

![Screenshot 2022-12-17 at 19 54 04](https://user-images.githubusercontent.com/114099418/208321865-1e5b2033-3fb8-4984-804b-de60af252274.png)

## Ad 3

Creating multi-stage Dockerfile:

Here I edited my Dockerfile like this:

![Screenshot 2022-12-18 at 22 52 54](https://user-images.githubusercontent.com/114099418/208321411-c42214c1-82ec-4724-a286-02457bb73506.png)

## Ad 4

Creating docker-compose configuration that will automatically start multiple containers:

My docker-compose.yml:

![Screenshot 2022-12-18 at 23 17 52](https://user-images.githubusercontent.com/114099418/208322334-5478e2fc-db40-4624-894e-f9f05e776aaa.png)

To start contariner I used ```docker-compose up``` 

Then I added a user to database to check if it is working correctly after restarting. To check it I tried to find my user in database and he was there:

<img width="712" alt="Screenshot 2022-12-18 at 23 33 52" src="https://user-images.githubusercontent.com/114099418/208322828-306136e2-75d5-4de9-a25a-334bcd4aac87.png">
