[![CircleCI](https://circleci.com/gh/feliperohdee/smallorange-cloudwatch-logger.svg?style=svg)](https://circleci.com/gh/feliperohdee/smallorange-cloudwatch-logger)

# Small Orange Cloudwatch Logger

##Compatible with just Node 7!!!!!!

Small helper to log into AWS Cloudwatch

## Features

- Creates Log Groups automatically
- Creates Log Streams automatically
- Automatic log batching
- JSON logging support
- Error logging support

## Usage

		const AWS = require('aws-sdk');
		const Logger = require('smallorange-cloudwatch-logger');

		AWS.config.update({
			accessKeyId: '{accessKeyId}',
			secretAccessKey: '{secretAccessKey}',
			region: '{region}'
		});

		const cloudWatchLogsClient = new AWS.CloudWatchLogs();
		const logger = new Logger({
			client: cloudWatchLogsClient,
			logGroupName: 'specGroup',
			debounceTime: 5000 // time to accumulate logs before write logs into CW
		});

		logger.log('test');
		logger.log(new Error('error'));
		logger.log({
			test: 'test'
		});

## Final Words

If you have any questions, contact me at felipe@smallorange.co.
