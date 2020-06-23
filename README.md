# dbscan - Allows scanning database rows into structs and more. 

## Overview [![GoDoc](https://godoc.org/github.com/georgysavva/dbscan?status.svg)](https://godoc.org/github.com/georgysavva/dbscan) [![Build Status](https://travis-ci.org/georgysavva/dbscan.svg?branch=master)](https://travis-ci.org/georgysavva/dbscan) [![Go Report Card](https://goreportcard.com/badge/github.com/georgysavva/dbscan)](https://goreportcard.com/report/github.com/georgysavva/dbscan)

## Install

```
go get github.com/georgysavva/dbscan
```

## Example

```
type User struct {
    ID    string `db:"user_id"`
    Name  string
    Email string
    Age   int
}

// Query rows from the database that implement dbscan.Rows interface, e.g. *sql.Rows:
db, _ := sql.Open("pgx", "example-connection-url")
rows, _ := db.Query(`SELECT user_id, name, email, age from users`)

var users []*User
if err := dbscan.ScanAll(&users, rows); err != nil {
    // Handle rows processing error
}
// users variable now contains data from all rows.
```

## License

MIT.
