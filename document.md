# Backend Documentation

## Login/Sigup Page

summary: This page is used to login or signup to the system

POST `/api/user/login`
body: {
    `user_name` : `str`
    `password` : `str`
}

response: 200
{
    `user_id` : `str`,
    `success` : `bool`
}

POST `/api/user/signup`
body: {
    `user_name` : `str`
    `password` : `str`
}

response: 200
{
    `user_id` : `str`,
    `success` : `bool`
}

> Notes: Frontend should check password strength

## Home Page (Dashboard)

summary: This page is used to display the **Total Amount** and **Friends List with Balance**

GET `/api/user/balance/:id`

response: 200
{
    `balance` : `int`
}

GET `/api/user/balance_list/:id`

response: 200
[
    {
        `friend_id` : `str`,
        `friend_name` : `str`,
        `balance` : `int`,
        `timestamp` : `date`
    }
]

## Friend Page

summary: This page is used to display the **Total Amount of a Friend** and **Transaction List with Balance** of a friend

GET `/api/friend/balance/:uid/:fid/`

response: 200
{
    `balance` : `int`,
}

GET `/api/friend/balance_list/:uid/:fid/`

response: 200
[
    {
        `transaction_id` : `str`,
        `balance` : `int`,
        `description` : `str`,
        `timestamp` : `date`,
    }
]

## Transaction Page

summary: This page is used to display the **Transaction List** of a friend

GET `/api/user/friends/:id/`

response: 200
[
    {
        `id` : `str`,
        `name` : `str`
    }
]

GET `/api/user/groups/:id/`

response: 200
[
    {
        `id` : `str`,
        `name` : `str`,
        `friends` : [
            {
                `id` : `str`,
                `name` : `str`
            }
        ]
    }
]

POST `/api/user/group/:id`
body {
    `name` : `str`,
    `friends` : [
        {
            `id` : `str`
        }
    ]
}

response: 200
[
    {
        `id` : `str`,
        `friends` : [
            {
                `id` : `str`,
                `name` : `str`
            }
        ]
    }
]

POST `/api/transaction/add/:id`
body {
    `description` : `str`,
    `transactions`: [
        `id` : `str`,
        `friends` : [
            `id` : `str`
        ],
        `amount` : `int`,
    ]
}

response: 200
{
    `id` : `str`,
    `success` : `bool`
}

## Timeline Page

summary: This page is used to display the **Transaction List** of a friend

GET `/api/user/timeline/:id/`

response: 200
[
    {
        `transaction_id` : `str`,
        `friend_id` : `str`,
        `balance` : `int`,
        `timestamp` : `date`
    }
]
