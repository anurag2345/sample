## Setup Instructions

Clone the repo from vcs(https://vcs.weberon.com/hg/Chatbot)

### Part A: Steps for Dialogflow
1. Goto project root floder and zip the folder agent-human-handoff-nodejs/spring_camp-intents
		`zip -r spring_camp-intents.zip agent-human-handoff-nodejs/spring_camp-intents`
1. Log in to the [Dialogflow Console](https://console.api.ai).
1. Create a new agent using the dropdown at the top of the left hand menu, next to the gear icon.
If the menu is not visible, click the icon with three horizontal lines to open it.
1. Type a name for your agent. Any name will work, but `agent-human-handoff-sample` is suggested.
1. Click `Save` to save the project, and wait for it to complete.
1. Click the gear icon near the top of the menu to see the project settings.
1. Click the `Export and Import` tab.
1. Click `RESTORE FROM ZIP`. Follow the directions to restore intents and entities from the
spring_camp-intents.zip file we just created.

### Part B: Steps for Node.js
1. Download and install nodejs by following instructions on [nodejs website](https://nodejs.org)
1. Ensure at least Node.js v6.9.1 is installed.
1. Within the repo directory, type `npm install` to install all of the project's dependencies.
1. To connect to your agent, you will need your Dialogflow client access token. To obtain it, open the project you
created in *Part A* in the Dialogflow console. Click the gear icon near the top of the menu to see the
project settings. Copy the `Client access token` from the `API keys` section of the `General` tab.
1. Set this value for variable `DIALOG_FLOW_APIAI_ACCESS_TOKEN` in file config.js.
1. To start the server, enter `npm start` from within the repo root directory.
1. You should see the text `Listening on *:3000`. The server is now ready to use.

**Note:** If you see the error `Error: listen EADDRINUSE :::3000` when starting the server, there is
already a process listening on port 3000 on your system. Identify and close that process, or edit `app.js`
to connect to a different port.

### Part C: Firebase instructions:
1. Login to firebase(https://console.firebase.google.com)
1. Create new firebase project by clicking on `Add Project` link.
1. To connect to firebase, you will need your firebase client access token. To obtain it, open the project you
just created firebase console. Click the gear icon near the top of the menu to see the
project settings. Copy the `Web API Key` and the `Project ID` from the `General` tab in `Project Settings`.
1. In file config.js update following lines
    `FIREBASE_API_KEY: '<API_KEY>',`
    `FIREBASE_AUTH_DOMAIN: "<PROJECT_ID>.firebaseapp.com",`
    `FIREBASE_DATABASEURL: "https://<PROJECT_ID>.firebaseio.com/",`
1. Click on Devlop tab in the left pane, and select Authentication
1. Click on `SIGN-IN METHOD` then select `Email/Password`.
1. Enable it, then click `SAVE`. (DONOT enable Email link).
1. Click `USERS` tab, then click on `ADD USER`.
1. Enter email and password, then click `ADD USER`.
1. Update the email-id and password in the config.js file
   `FIREBASE_EMAIL_ID: `
   `FIREBASE_PASSWORD: `

### Part D: Plivo Instructions
1. Login to the [Plivo](https://manage.plivo.com/)
1. Update the following entries in config.js
	`PLIVO_AUTH_ID:`
	`PLIVO_AUTH_TOKEN:`
	`PLIVO_DEST_NO: <Number to which sms is to be sent>`
	`PLIVO_SRC_NO: <Number associated with account>`

### Part E: Update config.js
1. Open the file agent-human-handoff-nodejs/config.js and update following values
	`IS_HTTPS_ENABLED: <whether to enable https or not>`
	`PATH_TO_SSL_KEY: <path/to/ssl/key/file>`
	`PATH_TO_SSL_CERT: <path/to/ssl/cert/file>`
	`MAUTIC_URL: <mautic url for sendong email>`
	`DOMAIN: <ip where server is to be run>`

### Part F: Update AppConfig.js file
1. Open file agent-human-handoff-nodejs/static/AppConfig.js and update following values
	`DOMAIN: <ip where server is to be run>`
	`OPERATOR_GREETING: <message sent when esclated to operator>`
	`SEND_CUSTOMER_DELAY_MESSAGES: <whether send message to customer if they don't respond>`
	`SEND_OPERATOR_DELAY_MESSAGES: <whether send message to customer if operator doesn't respond>`
	`IDLE_CUSTOMER_WAIT_TIME: <number of milliseconds after which CUSTOMER_DELAY_MESSAGE is sent>`
	`IDLE_OPERATOR_WAIT_TIME: <number of milliseconds after which OPERATOR_DELAY_MESSAGE is sent>`


### Part G: Deploy on website
1. In the file chatbotui.html, update the variables `server`(where the chatbot is running) and `page`(url of page where chatbot is to be added)
1. Put this file in the projects home directory naming `script.js`
1. Add following line in the head tag of the html file where chatbot is to be added
   <script src="/script.js"></script>


