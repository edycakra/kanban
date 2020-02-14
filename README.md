# Kanban App - Server
Nama database wajib: kanban-beta-fox

BaseUrl: http://localhost:3000

## **Register**

Return json access token after user register

-   **URL**

    /register

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `password=[string]`\
      `username=[string]`\
      `email=[string]`\
      `first_name=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
            "id": 10,
            "username": "cakra",
            "email": "cakra@mail.com",
            "password": "$2a$10$itmrYQ7eyFU620cB2NFMU.day8697zPWIg6ubZbsFMHQEy5V/sVue",
            "updatedAt": "2020-02-14T16:51:48.871Z",
            "createdAt": "2020-02-14T16:51:48.871Z"
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
            "message": [
                "email already exists"
            ]
        }
        ```
## **Login**

Returns json access token data when user login

-   **URL**

    /login

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `email=[string]`\
      `password=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
            "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiZW1haWwiOiJjYWtyYUBtYWlsLmNvbSIsImlhdCI6MTU4MTY5OTIyNH0.R6KtnS5AUADIgmahXFm3tXyw9eltaIbItZqnrtIHDPg",
            "email": "cakra@mail.com",
            "isLogin": true
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
            "message": [
                "invalid email/password"
            ]
        }
        ```
## **Find All Task**

  Returns json data for all task for specific user id

- **Headers**

    Authorization: access_token

-   **URL**

    /tasks/:id

-   **Method:**

    `GET`

-   **URL Params**

    **Required:**

    None

-   **Data Params**

     None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
            "data": [
                {
                    "id": 4,
                    "title": "Add 4th Task",
                    "category": "DONE",
                    "UserId": 2,
                    "createdAt": "2020-02-13T23:20:22.433Z",
                    "updatedAt": "2020-02-14T00:06:38.006Z"
                },
                {
                    "id": 9,
                    "title": "new task",
                    "category": "BACKLOG",
                    "UserId": 2,
                    "createdAt": "2020-02-14T01:51:39.071Z",
                    "updatedAt": "2020-02-14T02:13:02.165Z"
                }                
            ]
        }
        ```

-   **Error Response:**

    -   **Code:** 401 NOT AUTHORIZED <br />
        **Content:**
        ```json
        {
            "message": [
                "jwt error"
            ]
        }
        ```