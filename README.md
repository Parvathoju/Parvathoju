import boto3

sns = boto3.client('sns')

def send_notification(event, context):
    user_id = event['user_id']
    message = event['message'] 

  # Custom notification logic here
  response = sns.publish(
        TopicArn='arn:aws:sns:us-east-1:123456789012:MyTopic',
        Message=message,
        Subject='Notification',
        MessageStructure='string'
    )

  return {
        'statusCode': 200,
        'body': f'Notification sent to user {user_id}'
    }

