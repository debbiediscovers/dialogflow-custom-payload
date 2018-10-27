# dialogflow-custom-payload
Cheatsheet of Custom Payload for Dialogflow and Chatfuel


**Redirect to Block**

This is my favourite Custom Payload to use. This redirects the user to an existing Chatfuel block.

If you manage multiple bots, keep the name of the Chatfuel block consistent for commonly used intents (e.g. “Hi”, “Bye”, “Stop”, “Unsubscribe”, “Help”). This allows you to reuse the Dialogflow intents across multiple Chatfuel bots.

```javascript
{
  "redirect_to_blocks": [
    "Welcome message"
  ]
}
```

Simply copy the code above and paste it into Dialogflow’s Custom Payload editor. Change the block name. Remember, block names are case sensitive.


**Set Attribute**
```javascript
{
  "set_attributes": {
    "attributeName": "some value"
  }
}
```

**Set two Attributes, Redirect to Block**
```javascript
{
  "set_attributes": {
    "attributeName": "some value",
    "attributeName2": "some other value"
  },
  "redirect_to_blocks": [
    "Welcome message"
  ]
}
```

**Send Text then Redirect to Block**
```javascript
{
  "messages": [
    {
      "text": "Insert Random Text Here"
    }
  ],
  "redirect_to_blocks": [
    "Welcome message"
  ]
}
```

**Send Text with two Quick Replies**
```javascript
{
  "messages": [
    {
      "text": "Random text inserted here",
      "quick_replies": [
        {
          "title": "Quick Reply Button Name",
          "block_names": [
            "Chatfuel Block Name - Case Sensitive"
          ]
        },
        {
          "title": "Quick Reply Button Name",
          "block_names": [
            "Chatfuel Block Name - Case Sensitive"
          ]
        }
      ]
    }
  ]
}
```

**Send Text with three Quick Replies**
```javascript
{
  "messages": [
    {
      "text": "Insert Random Text Here",
      "quick_replies": [
        {
          "title": "Quick Reply Button Name",
          "block_names": [
            "Chatfuel Block Name - Case Sensitive"
          ]
        },
        {
          "title": "Quick Reply Button Name",
          "block_names": [
            "Chatfuel Block Name - Case Sensitive"
          ]
        },
        {
          "title": "Quick Reply Button Name",
          "block_names": [
            "Chatfuel Block Name - Case Sensitive"
          ]
        }
      ]
    }
  ]
}
```

**Send Image / Gif**
```javascript
{
  "messages": [
    {
      "attachment": {
        "type": "image",
        "payload": {
          "url": "https://media.giphy.com/media/yourgif.gif"
        }
      }
    }
  ]
}
```

**Send Image / Gif followed by Text**
```javascript
{
  "messages": [
    {
      "attachment": {
        "type": "image",
        "payload": {
          "url": "https://media.giphy.com/media/yourgif.gif"
        }
      }
    },
    {
      "text": "Insert Random Text Here"
    }
  ]
}
```

**Send Text followed by Image / Gif**
```javascript
{
  "messages": [
    {
      "text": "Insert Random Text Here"
    },
    {
      "attachment": {
        "type": "image",
        "payload": {
          "url": "https://media.giphy.com/media/yourgif.gif"
        }
      }
    }
  ]
}
```

**Send Text with three Buttons**
```javascript
{
  "messages": [
    {
      "attachment": {
        "type": "template",
        "payload": {
          "template_type": "button",
          "text": "Insert Random Text Here",
          "buttons": [
            {
              "type": "show_block",
              "block_names": [
                "Insert Chatfuel Block Name - Case Sensitive"
              ],
              "title": "Gallery Button Name"
            },
            {
              "type": "show_block",
              "block_names": [
                "Insert Chatfuel Block Name - Case Sensitive"
              ],
              "title": "Gallery Button Name"
            },
            {
              "type": "show_block",
              "block_names": [
                "Insert Chatfuel Block Name - Case Sensitive"
              ],
              "title": "Gallery Button Name"
            }
          ]
        }
      }
    }
  ]
}
```

**Send Gallery Button with URL**
```javascript
{
  "messages": [
    {
      "attachment": {
        "type": "template",
        "payload": {
          "template_type": "button",
          "text": "Insert Random Text Here",
          "buttons": [
            {
              "type": "web_url",
              "url": "https://yoursite.com",
              "title": "Insert Gallery Button Title"
            }
          ]
        }
      }
    }
  ]
}
```

**Send two Gallery Card with Square Image**
```javascript
{
 "messages": [
    {
      "attachment":{
        "type":"template",
        "payload":{
          "template_type":"generic",
          "image_aspect_ratio": "square",
          "elements":[
            {
              "title":"Insert Card Title",
              "image_url":"https://image.jpg",
              "subtitle":"Insert Subtitle",
              "buttons":[
                {
                  "type":"web_url",
                  "url":"https://yoursite.com",
                  "title":"Insert Button Title"
                }
              ]
            },
            {
              "title":"Insert Card 2 Title",
              "image_url":"https://image2.jpg",
              "subtitle":"Insert Subtitle 2",
              "default_action": {
                "type": "web_url",
                "url": "https://yoursite.com",
                "messenger_extensions": true
              },
              "buttons":[
                {
                  "type":"web_url",
                  "url":"https://yoursite.com",
                  "title":"Insert Button Title 2"
                }
              ]
            }
          ]
        }
      }
    }
  ]
}
```
