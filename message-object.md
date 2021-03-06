# Message Object

Regardless what platform you are targeting the bot for, the framework gives you a message object with same format.

An example JSON data for a `facebook` message is:

```
{
  timestamp: 1494895687121,
  text: 'who are you?',
  sender: '1223182967789737',
  rawBody: {
      sender: {
        id: '1223182967789737'
      },
      recipient: { id: '769372433211496' },
      timestamp: 1494892213769,
      message:{
        mid: 'mid.$cAAK7vV_yB-5iP8o-CVcDoT1gIade',
        seq: 11504,
        text: 'who are you?'
      }
  }
}

```

From the bot itself, developers can access the message object properties via `args` in the following way:

```
export class Bot {
    private args: any;

    constructor(args){
        this.args = args;
    }

    execute(){
        let text = this.args.text;
        let sender = this.args.sender;

        return new Promise((resolve)=>{
            resolve({
                tex: `I am resolved for ${sender} with ${text}`   
            });
        });
    }
}
```

The common definition of a message object regardless of its underlying platform is:

```
{
  timestamp : "number",
  sender : "object"
  text : "string"
  rawBody : "object"
  attachment: "object"
}

```

**Definition of Properties**:

* sender - Unique sender ID.
* text - User input text.
* rawBody - Original payload for the message.
* attachment - Links or image url.


An example of an attachment object (`facebook`):

```
"attachment": {
   "type": "image",
   "payload": {
     "url": "https://petersapparel.parseapp.com/img/shirt.png",
     "is_reusable": true
   }
 }

```
