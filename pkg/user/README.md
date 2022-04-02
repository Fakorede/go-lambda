
# go-lambda

> A simple serverless microservice built with Lambda, DynamoDB, and API Gateway


## Deplyment process

- Build application, then zip the build folder

```
GOARCH=amd64 GOOS=linux go build -o build/main cmd/main.go
chmod +x main
zip build/main.zip build/main
```

- Deploy to the Mangt Console (Create function and upload zip file, Create DynamoDB table, Create API Gateway and point it to the lambda function)

- Test Endpoints

```
curl --header "Content-Type: application/json" --request POST --data '{"email": "fab@thefabdev.com", "first_name": "Fab", "last_name": "Dev"}' https://ft20f9aquj.execute-api.us-east-1.amazonaws.com/staging
curl -X GET https://ft20f9aquj.execute-api.us-east-1.amazonaws.com/staging
curl -X GET https://ft20f9aquj.execute-api.us-east-1.amazonaws.com/staging\?email\=fab@thefabdev.com
curl --header "Content-Type: application/json" --request PUT --data '{"email": "fab@thefabdev.com", "first_name": "Fab", "last_name": "Dev"}' https://ft20f9aquj.execute-api.us-east-1.amazonaws.com/staging
curl -X DELETE https://ft20f9aquj.execute-api.us-east-1.amazonaws.com/staging\?email\=fab@thefabdev.com
```