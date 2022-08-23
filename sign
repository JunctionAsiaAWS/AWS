var AWS = require('aws-sdk')

AWS.config.update({
    region: 'ap-northeast-2',
    endpoint: "http://dynamodb.ap-northeast-2.amazonaws.com"
})

const docClient = new AWS.DynamoDB.DocumentClient();

exports.handler = function(event, context, callback) {
    const operation = event.httpMethod;
    switch (operation) {
        case 'POST':
            var params = {
                TableName: "teacher",
                Item: {
                    "id": event.id,
                    "name": event.name,
                    "password": event.password,
                    "email": event.email
                }
            };

            docClient.put(params, function(err, data) {
                if(err){
                    callback(err, null);
                } else{
                    callback(null, data);
                }
            })
            break;
        default:
            callback(new Error(`Operation Error`));
   }
}
