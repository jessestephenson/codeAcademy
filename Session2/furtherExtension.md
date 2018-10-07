# Code Academy: Session 3 Extended
> Using logic and variables to make a new intent!

## Introduction
So we've now looked at some basic nodeJS, we know how to make variables and use them a bit. We've made some functions. And more recently looked at some logic in NodeJS.

## Intents

### Starting with handler.js
We have the code from last time still available at https://github.com/N0nny/codeAcademy/blob/master/Session1/handler.js. You might notice that some code has been removed since we first used it.

It still contains the ```greetUser``` intent, but now we'll have a go at building on that.

First I'll explain what's going on in ```greetUser``` then we'll have a go at building a second intent.

```javascript
'use strict';

// --------------- Lex bot helper functions -----------------------
function close(sessionAttributes, fulfillmentState, message) {
    return {
        sessionAttributes,
        dialogAction: {
            type: 'Close',
            fulfillmentState,
            message,
        },
    };
}

// --------------- Functions that control the bot's behavior -----------------------
/**
 * Performs dialog management and fulfillment for greeting user.
 *
 */
function greetUser(intent_request, callback){
    var user_name = intent_request['currentIntent']['slots']['Name']
    var output_session_attributes = {
        "Name" : user_name
    }

    callback(close(output_session_attributes, 'Fulfilled',
    { contentType: 'PlainText', content: selectGreeting(user_name)}));
}


function selectGreeting(user_name){
    var options = [`Hi there ${user_name}, nice to meet you!`,
        `Hello ${user_name}, I hope you've enjoyed this lab session today!`,
        `Hey ${user_name}, hope you've had a good day!`];
    console.log(options[Math.floor(Math.random()*options.length)]);
    return options[Math.floor(Math.random()*options.length)];
}


 // --------------- Intents -----------------------

/**
 * Called when the user specifies an intent for this skill.
 */
function dispatch(intentRequest, callback) {
    console.log(`dispatch userId=${intentRequest.userId}, intentName=${intentRequest.currentIntent.name}`);

    const intentName = intentRequest.currentIntent.name;

    // Dispatch to your skill's intent handlers
    if (intentName === 'GreetUser'){
        return greetUser(intentRequest, callback);
    }
    throw new Error(`Intent with name ${intentName} not supported`);
}

// --------------- Main handler -----------------------

// Route the incoming request based on intent.
// The JSON body of the request is provided in the event slot.
module.exports.handler = (event, context, callback) => {
    try {
        // By default, treat the user request as coming from the America/New_York time zone.
        process.env.TZ = 'Pacific/Auckland';
        console.log(`event.bot.name=${event.bot.name}`);

        dispatch(event, (response) => callback(null, response));
    } catch (err) {
        callback(err);
    }
};
```

Starting from the bottom, the main handler ```module.exports.handler``` is a bit complicated and looks like there's a lot going on. But essentially what's happening is when this Lambda is called, it goes into here, and then it pushes the event information on to the ```dispatch``` function. And it does this using the parameters/arguments stuff we talked about last session.

```javascript
dispatch(intentRequest, callback)
```

The ```intentRequest``` is just the event object that triggered the lambda.
The ```callback``` is something that is called at the completion of a task, giving you the ability to pass a function to another function. If you want to read more about it go here:
>https://medium.com/@saurabhkumar_4718/node-js-callback-861f29642190 or
https://medium.com/@fotios.floros/explaining-javascript-callbacks-3d5a9ad52819

In the ```dispatch``` function, we first log the userId, this is just for debugging/ general logging purposes.
Then we pull the ```intentName``` from the intentRequest by accessing the key in the object, and then pulling its name.

Then we have our ```if``` statement, this is how we decide which intent to run. We only have the one intent currently, but to add another, we'd need to add another ```else if``` statement here so we can route the logic to the right function.

We then leave the logic check by calling ```greetUser()``` because that is what Lex told us the intent was ```GreetUser```. 
