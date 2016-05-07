# BitBucket Webhooks

## Summary

An implementation of all the BitBucket webhook API types in Go (golang) and
an HTTPHandler that can receive all the webhook events and call callbacks. This
is not a stable API. Submit issues if you have any problems or have suggestions.

## Install

```
go get gopkg.in/skyec/bitbucket-webhooks-v0
```

## Usage

```
wh := bitbucket.NewWebhook()
wh.Handle("repo:push", func(headers bitbucket.Headers, event interface{}) error {
  pe := event.(*bitbucket.PushEvent)
  log.Println("Repo name:", pe.Repository.Name)
  return nil
})

http.Handle("/webhooks", wh)
```
Start your server and enter "http(s)://yourserver/webhooks" in BitBucket
webhook interface. See the [BitBucket API webhooks docks](https://confluence.atlassian.com/bitbucket/manage-webhooks-735643732.html) for more.




##  Legal

Copyright (c) 2016 Skye Cove

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
