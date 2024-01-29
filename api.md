# API Docs

The backend is available at
- https://backend.intensivkontakt-staging.de on the STAGING environment, and
- https://backend.intensivkontakt.de on the PRODUCTION environment

The frontend should not use these URLs directly, but rather resolve the evironment variable `REACT_APP_BACKEND_URL` which will be set accordingly on each environment.
Please note that all URLs always end in a trailing slash!

## Authenticate user
```
POST /api/v1/auth/jwt/create/
```
- Authentication is performed based on `email` and `password` and both are exchanged for a JWT.

### Sample Request + Response
```http
POST /api/v1/auth/jwt/create/ HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 76
Content-Type: application/json
Host: backend.intensivkontakt-staging.de
User-Agent: HTTPie/2.6.0

{
    "email": "schwerin@intensivkontakt-staging.de",
    "password": "testtest123+"
}

HTTP/1.1 200 OK
Allow: POST, OPTIONS
Connection: keep-alive
Content-Length: 589
Content-Type: application/json
Date: Sun, 23 Jan 2022 08:34:40 GMT
Referrer-Policy: same-origin
Server: gunicorn
Vary: Cookie, Origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ1NTE4ODgwLCJpYXQiOjE2NDI5MjY4ODAsImp0aSI6ImU1NjBlNzg2ODM0YTQ4YjVhMTczZGRhNWMxM2MwMTgzIiwidXNlcl9pZCI6MTEsImlzcyI6IklLIiwic3ViIjoic2Nod2VyaW5AaW50ZW5zaXZrb250YWt0LXN0YWdpbmcuZGUiLCJhdWQiOiJJSyIsInNjb3BlIjpbXX0.sYoNI5szBB7O4O6UoiuodXlVljJ3wZKrl84m7acc_eo",
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY0MzAxMzI4MCwiaWF0IjoxNjQyOTI2ODgwLCJqdGkiOiIxNGJjZmRmZjM5NjE0Y2M3YWE1MGI1OTc1MzkzZGI0ZSIsInVzZXJfaWQiOjExfQ.tq1giIvqeYJtAKrwnZ183gu1C_B8V_qmaXT25hkfTw0"
}
```

## Get currently logged-in user
```
GET /api/v1/auth/users/me/
```
- Requires authentication.

### Sample Request + Response
```http
GET /api/v1/auth/users/me/ HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ1NTE4ODgwLCJpYXQiOjE2NDI5MjY4ODAsImp0aSI6ImU1NjBlNzg2ODM0YTQ4YjVhMTczZGRhNWMxM2MwMTgzIiwidXNlcl9pZCI6MTEsImlzcyI6IklLIiwic3ViIjoic2Nod2VyaW5AaW50ZW5zaXZrb250YWt0LXN0YWdpbmcuZGUiLCJhdWQiOiJJSyIsInNjb3BlIjpbXX0.sYoNI5szBB7O4O6UoiuodXlVljJ3wZKrl84m7acc_eo
Connection: keep-alive
Host: backend.intensivkontakt-staging.de
User-Agent: HTTPie/2.6.0

HTTP/1.1 200 OK
Allow: GET, PUT, PATCH, DELETE, HEAD, OPTIONS
Connection: keep-alive
Content-Length: 109
Content-Type: application/json
Date: Sun, 23 Jan 2022 08:56:54 GMT
Referrer-Policy: same-origin
Server: gunicorn
Vary: Cookie, Origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "email": "schwerin@intensivkontakt-staging.de",
    "first_name": "Test",
    "id": 11,
    "last_name": "Test",
    "station": null
}
```

## Get hospitals for hospital admin
```
GET /api/v1/contacts/hospitals/
```
- Requires authentication.

### Sample Request + Response
```http
GET /api/v1/contacts/hospitals/ HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ1NTE4ODgwLCJpYXQiOjE2NDI5MjY4ODAsImp0aSI6ImU1NjBlNzg2ODM0YTQ4YjVhMTczZGRhNWMxM2MwMTgzIiwidXNlcl9pZCI6MTEsImlzcyI6IklLIiwic3ViIjoic2Nod2VyaW5AaW50ZW5zaXZrb250YWt0LXN0YWdpbmcuZGUiLCJhdWQiOiJJSyIsInNjb3BlIjpbXX0.sYoNI5szBB7O4O6UoiuodXlVljJ3wZKrl84m7acc_eo
Connection: keep-alive
Host: backend.intensivkontakt-staging.de
User-Agent: HTTPie/2.6.0

HTTP/1.1 200 OK
Allow: GET, HEAD, OPTIONS
Connection: keep-alive
Content-Length: 1635
Content-Type: application/json
Date: Sun, 23 Jan 2022 08:38:21 GMT
Referrer-Policy: same-origin
Server: gunicorn
Vary: Cookie, Origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "count": 1,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 2,
            "logo": "https://int-stg-core-storage.s3.amazonaws.com/hospital_logos/150288236-02d66b9e-0ad1-4368-a9db-c9bcc527b4b2.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIARVBTQLA67AB5AWG2%2F20220123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20220123T083821Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEC4aDGV1LWNlbnRyYWwtMSJHMEUCIQCBMakj2uPbAezuTLxAEsbQbtcpGoZ4f8Bx4ge%2F2AmxUgIgPYb7AXFVFKSDh8i4BhMZ4pb1lpJL1N6EGxE2xA90vboqiAQIVxAAGgwxMTM5MjQ2NTkyNjEiDKbGo3GQFDa7nJnuUyrlAxQC6faCPlhvk0qQlTzSn6WtVfjTUQsgI2E%2B7R0l1Qd9hR%2F9gMkBvD%2FN%2BWn94gXKTVrDp8v8410s1bakpDS%2BdjTNpJxxS0CWquV06kLclcPw9ZapTzXMQSjfsljNVpbmKy%2Foau52NMQLpVJp4BE7R3XOmVrT4Of6raCtTBYXzqWo89SAPdJhao5YOxPYaH5OryGLxVK21f8062o773zFUC3AoLHZ8kLEcpUTdgZLNmfUPlO1oMj4K9z4gYA59vT8JlSmn43n9I9sWDh4qtsZdQgwuWPrSJ6YcpkFrlNJr6BHxFCOWu1VigKrtmPPwG0WozmRdwfu7e%2Bs7ebm%2BVbrCscT0IhE%2B5Ja2dNN45JvpJcwkKjT%2BDn0YWN6JC8%2FSeXLzUJPyeQxnhqJlsQLvoMvVqlHk8d9FhbPpvq7M8Ma2KZ6kum%2F0kccRWZOlK5YVW%2BWummDpc6utVJCFgaYzzl8VVT79OaFf6%2BJDvB0eSA9zpcS%2FOrz73xxSXKby61lLPd5UY5W3MSIG7EccQYqMsrcD2i7%2F%2FvBjU2Y1j2WjDwatOtmF06wbpKjSIIXgp752VP%2BDscbxDN9yvl04tw3tpv9vAKH59eQPLKQJQv3sZ3qOs1akvgErNNXJbEEonEJE7Ih%2BQJhv2FSMP%2Fks48GOqUBsX1yHSs8bgoYQSd5XXOB8GV9%2F1OdIA3r6kE6sZIPJgTMbYzLQFL19hUwQ6oUMNiKB2VenjXvSTjLuD0hFmSuOn9oB5gi71pLyDkaxGPIqv6bPfjMaaM3xqzD3HyCpFlOpPkm1bQ2%2BB4SyUq4%2FK4PPRZV498EjDviIAgCwzLOWTN2Y6zeqUvBaMSQicy05cF90ffniZN8T%2FaXAJkuqgh6XCSI0nA8&X-Amz-Signature=99c0d2322291a09548566dc8c91c70d886fc2531986a76bf4bcd920a33d65ff1",
            "manager": 11,
            "name": "Helios Kliniken Schwerin"
        }
    ]
}
```

## Get all stations the requesting user has access to
```
GET /api/v1/contacts/stations/
```
- Requires authentication

### Sample Request + Response
```http
GET /api/v1/contacts/stations/ HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ1NTE4ODgwLCJpYXQiOjE2NDI5MjY4ODAsImp0aSI6ImU1NjBlNzg2ODM0YTQ4YjVhMTczZGRhNWMxM2MwMTgzIiwidXNlcl9pZCI6MTEsImlzcyI6IklLIiwic3ViIjoic2Nod2VyaW5AaW50ZW5zaXZrb250YWt0LXN0YWdpbmcuZGUiLCJhdWQiOiJJSyIsInNjb3BlIjpbXX0.sYoNI5szBB7O4O6UoiuodXlVljJ3wZKrl84m7acc_eo
Connection: keep-alive
Host: backend.intensivkontakt-staging.de
User-Agent: HTTPie/2.6.0

HTTP/1.1 200 OK
Allow: GET, HEAD, OPTIONS
Connection: keep-alive
Content-Length: 93
Content-Type: application/json
Date: Sun, 23 Jan 2022 15:36:27 GMT
Referrer-Policy: same-origin
Server: gunicorn
Vary: Cookie, Origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "count": 1,
    "next": null,
    "previous": null,
    "results": [
        {
            "hospital": 2,
            "id": 1,
            "name": "Station 01"
        }
    ]
}
```

## Get all active patients
```
GET /api/v1/contacts/patients/
```
- Requires authentication.

### Sample Request + Response
```http
GET /api/v1/contacts/patients/ HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjQ1NTE4ODgwLCJpYXQiOjE2NDI5MjY4ODAsImp0aSI6ImU1NjBlNzg2ODM0YTQ4YjVhMTczZGRhNWMxM2MwMTgzIiwidXNlcl9pZCI6MTEsImlzcyI6IklLIiwic3ViIjoic2Nod2VyaW5AaW50ZW5zaXZrb250YWt0LXN0YWdpbmcuZGUiLCJhdWQiOiJJSyIsInNjb3BlIjpbXX0.sYoNI5szBB7O4O6UoiuodXlVljJ3wZKrl84m7acc_eo
Connection: keep-alive
Host: backend.intensivkontakt-staging.de
User-Agent: HTTPie/2.6.0

HTTP/1.1 200 OK
Allow: GET, POST, HEAD, OPTIONS
Connection: keep-alive
Content-Length: 373
Content-Type: application/json
Date: Sun, 23 Jan 2022 19:54:08 GMT
Referrer-Policy: same-origin
Server: gunicorn
Vary: Cookie, Origin
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "count": 2,
    "next": null,
    "previous": null,
    "results": [
        {
            "date_of_admission": "2022-01-23",
            "date_of_birth": "1970-01-01",
            "first_name": "Anna",
            "gender": "W",
            "id": 1,
            "last_asset_added": null,
            "last_name": "Müller",
            "station": 1
        },
        {
            "date_of_admission": "2022-01-23",
            "date_of_birth": "1980-01-01",
            "first_name": "Erik",
            "gender": "M",
            "id": 2,
            "last_asset_added": null,
            "last_name": "Meyer",
            "station": 1
        }
    ]
}
```
