# JWT Sample Application
### Includes:

- Java 17
- Spring Boot 3.0.1
- JJWT API 0.11.5
- PostgreSQL (JDBC 42.5.1)

<br/>

### Endpoints:
To test <br>
`/api/test/all` <br>
`/api/test/user` <br>
`/api/test/mod` <br>
`/api/test/admin` <br>

To control <br>
`/api/auth/signin` <br>
`/api/auth/signup` <br>

<br>

### Usage

With having database (configurations in `application.yaml`), execute queries below and we can run the application.

```sql
INSERT INTO roles(name) VALUES('ROLE_USER');
INSERT INTO roles(name) VALUES('ROLE_MODERATOR');
INSERT INTO roles(name) VALUES('ROLE_ADMIN');
```
<br> <br>
After that, send a request to create a user:

`POST` <br>
`localhost:8080/api/auth/signup`
```json
{
    "username": "atif",
    "email": "me@atif.dev",
    "password": "123456",
    "role": ["mod", "user"]
}
```
<br> <br>
Then you can log in and get the auth token:

`POST` <br>
`localhost:8080/api/auth/signin`
```json
{
    "username": "atif",
    "password": "123456"
}
```
<br> <br>

`all` endpoint is public.

With the token, now you can access the `user` and `mod` endpoints, but not the `admin`. Because we created the user with these two roles.