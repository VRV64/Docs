# Web Requests

Sends a HTTP web request to the specified URL. Returns true if the web request was sent, false if not. The callback is called with 2 parameters - an integer HTTP response code and a string response.

## Get method

``` csharp
using Oxide.Core;
using Oxide.Core.Libraries;

namespace Oxide.Plugins
{
    [Info("EpicPlugin", "Unknown", 1.0)]
    [Description("This example illustrates how to use a GET WebRequest.")]

    class EpicPlugin : RustPlugin
    {
        [ChatCommand("getrequest")]
        void GetRequest(BasePlayer player, string command, string[] args)
        {
            var WebRequestsGet = new WebRequests();
			WebRequestsGet.EnqueueGet("http://www.google.com/search?q=oxide", (code, response) => GetCallback(code, response, player), this);
        }

        void GetCallback(int code, string response, BasePlayer player)
        {
            if (response == null || code != 200)
            {
                Puts("Couldn't get an answer from Google for " + player.displayName);
                return;
            }
            Puts("Google answered for " + player.displayName + ": " + response);
        }
    }
}
```

``` lua
webrequests.EnqueueGet("http://www.google.com/search?q=oxide", function(code, response)
    if response == nil or code ~= 200 then 
        print("Couldn't get an answer from Google!") 
        return 
    end
    print("Google answered: " .. tostring(response))
end, self.Plugin)
```

``` javascript
webrequests.EnqueueGet("http://www.google.com/search?q=oxide", function(code, response) {
    if (response == null || code != 200) {
        print("Couldn't get an answer from Google!");
        return
    }
    print("Google answered: " + response);
}.bind(this), this.Plugin);
```

``` coffeescript
We need a CoffeeScript example here
```

``` python
from System import Action, Int32, String
def response_handler(code, response):
    if response == None or code != 200:
        print "Couldn't get an answer from Google!" 
        return 
    print "Google answered: " + response
webrequests.EnqueueGet("http://www.google.com/search?q=oxide", Action[Int32,String](response_handler), self.Plugin);
```

This uses the raw connection to a web page as you would on your browser.

Returns true/false

## Post method

``` csharp
using Oxide.Core;
using Oxide.Core.Libraries;

namespace Oxide.Plugins
{
    [Info("EpicPlugin", "Unknown", 1.0)]
    [Description("This example illustrates how to use a POST WebRequest.")]
    class EpicPlugin : RustPlugin
    {
        [ChatCommand("postrequest")]
        void PostRequest(BasePlayer player, string command, string[] args)
        {
            webrequests.EnqueuePost("http://www.google.com/search?q=oxide", "param1=value1&param2=value2", (code, response) => PostCallback(code, response, player), this);
        }

        void PostCallback(int code, string response, BasePlayer player)
        {
            if (response == null || code != 200)
            {
                Puts("Couldn't get an answer from Google for " + player.displayName);
                return;
            }
            Puts("Google answered for " + player.displayName + ": " + response);
        }
    }
}
```

``` lua
We need a Lua example here
```

``` javascript
We need a JavaScript example here
```

``` coffeescript
We need a CoffeeScript example here
```

``` python
We need a Python example here
```

Returns true/false
