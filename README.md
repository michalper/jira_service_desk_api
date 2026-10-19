# jira_service_desk_api

Unofficial PHP client for the Jira Service Desk Cloud REST API (basic auth).

## Install

```bash
composer require michalper/jira_service_desk_api
```

## Usage

```php
$client = new JiraServiceDesk();
$client->setHost('https://your-domain.atlassian.net')
    ->setUsername('...')
    ->setPassword('...');

$client->request->createCustomerRequest($requestModel);
$requests = $client->request->getMyCustomerRequests();
$request = $client->request->getCustomerRequestByIdOrKey('HELP-1');

$client->request->createRequestComment('HELP-1', 'Looking into it', $public = true);
$client->request->getRequestComments('HELP-1');

$client->request->addRequestParticipants('HELP-1', ['jdoe']);
$client->request->getSlaInformation('HELP-1');
$client->request->createAttachment('HELP-1', $attachmentModel);
```

`request` covers customer requests, comments, participants, SLA tracking and attachments against the [Jira Service Desk Cloud REST API](https://docs.atlassian.com/jira-servicedesk/REST/cloud/); `servicedesk` and `info` cover service desk metadata.

## License

GNU GPL
