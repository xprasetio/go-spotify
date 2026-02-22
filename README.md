# Golang Spotify

Golang REST API With gin framework and database postgreSQL

## [Go-Spotify](https://github.com/xprasetio/go-spotify)

## Table of Contents

- [Getting Started](#getting-started)
- [Structures](#structures)
- [Features](#features)
  - [API Response](#api-endpoint)
  - [Sign Up response](#signup-response)
  - [Login response](#login-response)
  - [Track Search response](#track-search-response)
- [Credits](#credits)
- [Copyright](#copyright)

## Getting Started

#### Requirements

- Database: `Postgres`
- Docker
- Viper
- Gin
- Go v1.22.x

#### Install & Run

Download this project:

```shell script
git clone https://github.com/xprasetio/go-spotify.git
```

Download project dependencies:

```shell script
go mod download && go mod tidy
```

Before run this project, you should set configs with yours.
Create & configure your `config.yaml` or with my setting config smtp with gmails mtp

Fast run with:

```shell script
make run

# running on default port 9999
```

Build with docker for the database `postgreeSQL`

```shell script
docker-compose up -d
```

## Structures

```
├── cmd
│   └── main.go
├── docker-compose.yml
├── go.mod
├── go.sum
├── internal
│   ├── configs
│   │   ├── config.go
│   │   ├── config.yaml
│   │   └── types.go
│   ├── handler
│   │   ├── memberships
│   │   │   ├── handler_mock_test.go
│   │   │   ├── handler.go
│   │   │   ├── login_test.go
│   │   │   ├── login.go
│   │   │   ├── signup_test.go
│   │   │   └── signup.go
│   │   └── tracks
│   │       ├── handler_mock_test.go
│   │       ├── handler.go
│   │       ├── recommendations_test.go
│   │       ├── recommendations.go
│   │       ├── search_test.go
│   │       ├── search.go
│   │       ├── track_activities_test.go
│   │       └── track_activities.go
│   ├── middleware
│   │   └── middleware.go
│   ├── models
│   │   ├── memberships
│   │   │   └── user.go
│   │   ├── spotify
│   │   │   └── spotify.go
│   │   └── trackactivities
│   │       └── trackactivities.go
│   ├── repository
│   │   ├── memberships
│   │   │   ├── repository.go
│   │   │   ├── users_test.go
│   │   │   └── users.go
│   │   ├── spotify
│   │   │   ├── outbound.go
│   │   │   ├── recommendations_test.go
│   │   │   ├── recommendations.go
│   │   │   ├── response.go
│   │   │   ├── search_test.go
│   │   │   ├── search.go
│   │   │   └── token.go
│   │   └── trackactivities
│   │       ├── repository.go
│   │       ├── trackactivities_test.go
│   │       └── trackactivities.go
│   └── service
│       ├── memberships
│       │   ├── login_test.go
│       │   ├── login.go
│       │   ├── service_mock_test.go
│       │   ├── service.go
│       │   ├── signup_test.go
│       │   └── signup.go
│       └── tracks
│           ├── recommendations_test.go
│           ├── recommendations.go
│           ├── search_test.go
│           ├── search.go
│           ├── service_mock_test.go
│           ├── service.go
│           ├── track_activities_test.go
│           └── track_activities.go
├── Makefile
├── pkg
│   ├── httpclient
│   │   ├── client_mock.go
│   │   └── client.go
│   ├── internalsql
│   │   └── sql.go
│   └── jwt
│       └── jwt.go
├── README.md
└── spotify_postgres
    └── db
```

## Features

### API Endpoint

All RESTful endpoint has `prefix` support. Prefix format is: /`memberships`/routes.

API endpoint design :

- `signup`
- `login`
- `tracks/search`

#### Signup Response

```shell script
curl --location 'localhost:9999/memberships/sign_up' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email" : "xprasetio@gmail.com",
    "username" : "xprasetio",
    "password" : "admin789"
}'
```

will return:

```json
{
  "message": "success"
}
```

#### Login Response

```shell script
curl --location 'localhost:9999/memberships/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email" : "xprasetio@gmail.com",
    "password" : "admin789"
}'
```

#### Track Search response

```shell script
curl --location 'localhost:9999/tracks/search?query=bohemian&pageSize=10&pageIndex=1' \
--header 'Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NzE2NzE3MDIsImlkIjoxLCJ1c2VybmFtZSI6ImFkbWluIn0.T3OfikSxtA2kakhMVaeLyBkIm5hAFWVs0u9ZPInDoCw' \
--data '
```

will return:

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NzE2NzE3MDIsImlkIjoxLCJ1c2VybmFtZSI6ImFkbWluIn0.T3OfikSxtA2kakhMVaeLyBkIm5hAFWVs0u9ZPInDoCw"
}
```

## Credits

- [Go](https://github.com/golang/go) - The Go Programming Language
- [gin](https://github.com/gin-gonic/gin) - Gin is HTTP web framework written in Go (Golang)
- [gorm](https://github.com/go-gorm/gorm) - The fantastic ORM library for Golang
- [viper](https://github.com/spf13/viper) - Complete configuration solution for Golang
- [docker](https://www.docker.com/products/docker-hub/) - Cloud Native a software development
- [gomock](https://github.com/uber-go/mock) - Mocking Framework Golang
- [spotify] (https://developer.spotify.com/documentation/web-api) - WEB API Spotify

## Copyright

Copyright (c) 2026 Eko Prasetio.
