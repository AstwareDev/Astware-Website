## **SentinelStore API Released**

We’re excited to officially launch the **SentinelStore API**, a lightweight and secure data management system built for real-time use with Roblox exploit clients. Designed with simplicity and performance in mind, SentinelStore allows individual exploiters to send, retrieve, and manage their session data using per-client **access keys**.

### How It Works

Each exploiter uses a unique `accessKey` to encrypt and retrieve their own isolated data. The API supports the following endpoints:

* `POST /send` — Save new data
* `POST /latest` — Get the latest saved entry
* `POST /all` — Get all entries for a key

All endpoints expect a JSON payload with your `accessKey` and data (if sending).

### Example (Send Data)

```lua
local HttpService = game:GetService("HttpService")

local accessKey = "your-secret-access-key"
local dataToSend = {
    health = 100,
    position = {x = 12, y = 4, z = 8},
    inventory = {"Sword", "Potion", "Key"}
}

local response = request({
    Url = "https://astware-sentinelapi.vercel.app/send",
    Method = "POST",
    Headers = {
        ["Content-Type"] = "application/json"
    },
    Body = HttpService:JSONEncode({
        accessKey = accessKey,
        data = dataToSend
    })
})

print("Server response:", response.Body)
```

### Example (Get Latest)

```lua
local response = request({
    Url = "https://astware-sentinelapi.vercel.app/latest",
    Method = "POST",
    Headers = {
        ["Content-Type"] = "application/json"
    },
    Body = HttpService:JSONEncode({
        accessKey = "your-secret-access-key"
    })
})

local result = HttpService:JSONDecode(response.Body)
print("Latest data:", result.data)
```

### Example (Get All Data)

```lua
local response = request({
    Url = "https://astware-sentinelapi.vercel.app/all",
    Method = "POST",
    Headers = {
        ["Content-Type"] = "application/json"
    },
    Body = HttpService:JSONEncode({
        accessKey = "your-secret-access-key"
    })
})

local result = HttpService:JSONDecode(response.Body)
for i, entry in ipairs(result.data) do
    print("Entry " .. i, entry)
end
```

### Auto-Cleanup

- To keep the API lightweight, **data older than 2 hours is automatically deleted** on every send or get request.

### Flaws
- You can't send Instances, CFrames and other roblox-only related stuff, you can only send strings, booleans and numbers.
