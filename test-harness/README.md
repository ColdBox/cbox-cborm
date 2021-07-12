# CBORM Test Suite

## Getting Started

Assuming you have both CommandBox and Docker installed:

1. Open CommandBox and `cd` to `test-harness/` - `box && cd test-harness`
2. Install test dependencies - `box install`
3. Start a test CF instance with the engine of your choice - `server start server-lucee@5.json`
4. Start up a MYSQL docker container pointing to `test-harness/tests/resources/db/` as the seeder script location:

```bash
docker run \
    -e MYSQL_ROOT_PASSWORD=ortussolutions \
    -e MYSQL_DATABASE=coolblog \
    -v "$PWD/test-harness/tests/resources/db/":/docker-entrypoint-initdb.d \
    -p 3306:3306 \
    --detach \
    --name cborm_mysql \
    mysql
```

5. Run tests and profit. 😁 `box testbox run` or `http://127.0.0.1:60299/tests/index.cfm`