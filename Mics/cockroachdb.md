
docker pull cockroachdb/cockroach 

docker run --name=db -p 26257 -p 8080 cockroachdb/cockroach start --insecure

docker exec -it db ./cockroach sql --insecure

create database ordersdb;


CREATE TABLE drivers (
    id UUID NOT NULL,
    city STRING NOT NULL,
    name STRING,
    dl STRING UNIQUE,
    address STRING,
    CONSTRAINT "primary" PRIMARY KEY (city ASC, id ASC)
);


create table orders (id string not null, customerid string, status string, createdon int, restaurantid string);
create table orderitems (orderid string not null, customerid string, code string, name string, unitprice int, quantity int); 