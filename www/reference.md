---
layout: layout.njk
title: </> htmx - Attributes
---


## Contents

* [htmx Core Attributes](#attributes)
* [htmx Additional Attributes](#attributes-additional)
* [htmx CSS Classes](#classes)
* [htmx Request Headers](#request_headers)
* [htmx Response Headers](#response_headers)
* [htmx Events](#events)
* [htmx Extensions](/extensions#reference)
* [Javascript API](#api)

## <a name="attributes"></a> [Core Attribute Reference](#attributes)

The following are the most common attributes when using htmx.

<div class="info-table">

| Attribute                                      | Description |
|------------------------------------------------|-------------|
| [`hx-boost`](/attributes/hx-boost)             | add or remove [progressive enhancement](https://en.wikipedia.org/wiki/Progressive_enhancement) for links and forms
| [`hx-get`](/attributes/hx-get)                 | issues a `GET` to the specified URL
| [`hx-post`](/attributes/hx-post)               | issues a `POST` to the specified URL
| [`hx-push-url`](/attributes/hx-push-url)       | pushes the URL into the browser location bar, creating a new history entry
| [`hx-select`](/attributes/hx-select)           | select content to swap in from a response
| [`hx-select-oob`](/attributes/hx-select-oob)   | select content to swap in from a response, out of band (somewhere other than the target)
| [`hx-swap`](/attributes/hx-swap)               | controls how content is swapped in (`outerHTML`, `beforeEnd`, `afterend`, ...)
| [`hx-swap-oob`](/attributes/hx-swap-oob)       | marks content in a response to be out of band (should swap in somewhere other than the target)
| [`hx-target`](/attributes/hx-target)           | specifies the target element to be swapped
| [`hx-trigger`](/attributes/hx-trigger)         | specifies the event that triggers the request
| [`hx-vals`](/attributes/hx-vals)               | adds values to the parameters to submit with the request (JSON-formatted)

</div>

## <a name="attributes-additional"></a> [Additional Attribute Reference](#attributes-additional)

The table below lists all other attributes available in htmx.

<div class="info-table">

| Attribute                                      | Description |
|------------------------------------------------|-------------|
| [`hx-confirm`](/attributes/hx-confirm)         | shows a `confim()` dialog before issuing a request
| [`hx-delete`](/attributes/hx-delete)           | issues a `DELETE` to the specified URL
| [`hx-disable`](/attributes/hx-disable)         | disables htmx processing for the given node and any children nodes
| [`hx-disinherit`](/attributes/hx-disinherit)   | control and disable automatic attribute inheritance for child nodes
| [`hx-encoding`](/attributes/hx-encoding)       | changes the request encoding type
| [`hx-ext`](/attributes/hx-ext)                 | extensions to use for this element
| [`hx-headers`](/attributes/hx-headers)         | adds to the headers that will be submitted with the request
| [`hx-history-elt`](/attributes/hx-history-elt) | the element to snapshot and restore during history navigation
| [`hx-include`](/attributes/hx-include)         | include additional data in requests
| [`hx-indicator`](/attributes/hx-indicator)     | the element to put the `htmx-request` class on during the request
| [`hx-params`](/attributes/hx-params)           | filters the parameters that will be submitted with a request
| [`hx-patch`](/attributes/hx-patch)             | issues a `PATCH` to the specified URL
| [`hx-preserve`](/attributes/hx-preserve)       | specifies elements to keep unchanged between requests
| [`hx-prompt`](/attributes/hx-prompt)           | shows a `prompt()` before submitting a request
| [`hx-put`](/attributes/hx-put)                 | issues a `PUT` to the specified URL
| [`hx-replace-url`](/attributes/hx-replace-url) | replace the URL in the browser location bar
| [`hx-request`](/attributes/hx-request)         | configures various aspects of the request
| [`hx-sse`](/extensions/server-sent-events)     | has been moved to an extension.  [Documentation for older versions](/attributes/hx-sse)
| [`hx-sync`](/attributes/hx-sync)               | control how requests made by different elements are synchronized
| [`hx-vars`](/attributes/hx-vars)               | adds values dynamically to the parameters to submit with the request (deprecated, please use [`hx-vals`](/attributes/hx-vals))
| [`hx-ws`](/extensions/web-sockets)             | has been moved to an extension.  [Documentation for older versions](/attributes/hx-ws)


</div>

## <a name="classes"></a> [CSS Class Reference](#classes)

<div class="info-table">

| Class | Description |
|-----------|-------------|
| `htmx-added` | Applied to a new piece of content before it is swapped, removed after it is settled.
| `htmx-indicator` | A dynamically generated class that will toggle visible (opacity:1) when a `htmx-request` class is present
| `htmx-request` | Applied to either the element or the element specified with [`hx-indicator`](/attributes/hx-indicator) while a request is ongoing
| `htmx-settling` | Applied to a target after content is swapped, removed after it is settled. The duration can be modified via [`hx-swap`](/attributes/hx-swap).
| `htmx-swapping` | Applied to a target before any content is swapped, removed after it is swapped. The duration can be modified via [`hx-swap`](/attributes/hx-swap).

</div>

## <a name="headers"></a> [HTTP Header Reference](#headers)

### <a name="request_headers"></a> [Request Headers Reference](#request_headers)

<div class="info-table">

| Header | Description |
|-------|-------------|
| `HX-Boosted` | indicates that the request is via an element using [hx-boost](/attributes/hx-boost)
| `HX-Current-URL` | the current URL of the browser
| `HX-History-Restore-Request` | `true` if the request is for history restoration after a miss in the local history cache
| `HX-Prompt` | the user response to an [hx-prompt](/attributes/hx-prompt)
| `HX-Request` | always `true`
| `HX-Target` | the `id` of the target element if it exists
| `HX-Trigger-Name` | the `name` of the triggered element if it exists
| `HX-Trigger` | the `id` of the triggered element if it exists

</div>

### <a name="response_headers"></a> [Response Headers Reference](#response_headers)

<div class="info-table">

| Header                                           | Description |
|--------------------------------------------------|-------------|
| [`HX-Location`](/headers/hx-location)            | Allows you to do a client-side redirect that does not do a full page reload
| [`HX-Push-Url`](/headers/hx-push-url)            | pushes a new url into the history stack
| `HX-Redirect`                                    | can be used to do a client-side redirect to a new location
| `HX-Refresh`                                     | if set to "true" the client side will do a a full refresh of the page
| [`HX-Replace-Url`](/headers/hx-replace-url)      | replaces the current URL in the location bar
| `HX-Reswap`                                      | Allows you to specify how the response will be swapped. See [hx-swap](/attributes/hx-swap) for possible values 
| `HX-Retarget`                                    | A CSS selector that updates the target of the content update to a different element on the page
| [`HX-Trigger`](/headers/hx-trigger)              | allows you to trigger client side events, see the [documentation](/headers/hx-trigger) for more info
| [`HX-Trigger-After-Settle`](/headers/hx-trigger) | allows you to trigger client side events, see the [documentation](/headers/hx-trigger) for more info
| [`HX-Trigger-After-Swap`](/headers/hx-trigger)   | allows you to trigger client side events, see the [documentation](/headers/hx-trigger) for more info

</div>

## <a name="events"></a> [Event Reference](#events)

<div class="info-table">

| Event | Description |
|-------|-------------|
| [`htmx:abort`](/events#htmx:abort) | send this event to an element to abort a request
| [`htmx:afterOnLoad`](/events#htmx:afterOnLoad) | triggered after an AJAX request has completed processing a successful response
| [`htmx:afterProcessNode`](/events#htmx:afterProcessNode) | triggered after htmx has initialized a node
| [`htmx:afterRequest`](/events#htmx:afterRequest)  | triggered after an AJAX request has completed
| [`htmx:afterSettle`](/events#htmx:afterSettle)  | triggered after the DOM has settled
| [`htmx:afterSwap`](/events#htmx:afterSwap)  | triggered after new content has been swapped in
| [`htmx:beforeOnLoad`](/events#htmx:beforeOnLoad)  | triggered before any response processing occurs
| [`htmx:beforeProcessNode`](/events#htmx:afterProcessNode) | triggered before htmx initializes a node
| [`htmx:beforeRequest`](/events#htmx:beforeRequest)  | triggered before an AJAX request is made
| [`htmx:beforeSwap`](/events#htmx:beforeSwap)  | triggered before a swap is done, allows you to configure the swap
| [`htmx:beforeSend`](/events#htmx:beforeSend)  | triggered just before an ajax request is sent
| [`htmx:configRequest`](/events#htmx:configRequest)  | triggered before the request, allows you to customize parameters, headers
| [`htmx:historyCacheError`](/events#htmx:historyCacheError)  | triggered on an error during cache writing
| [`htmx:historyCacheMiss`](/events#htmx:historyCacheMiss)  | triggered on a cache miss in the history subsystem
| [`htmx:historyCacheMissError`](/events#htmx:historyCacheMissError)  | triggered on a unsuccessful remote retrieval 
| [`htmx:historyCacheMissLoad`](/events#htmx:historyCacheMissLoad)  | triggered on a succesful remote retrieval 
| [`htmx:historyRestore`](/events#htmx:historyRestore)  | triggered when htmx handles a history restoration action
| [`htmx:beforeHistorySave`](/events#htmx:beforeHistorySave)  | triggered before content is saved to the history cache
| [`htmx:load`](/events#htmx:load)  | triggered when new content is added to the DOM
| [`htmx:noSSESourceError`](/events#htmx:noSSESourceError)  | triggered when an element refers to a SSE event in its trigger, but no parent SSE source has been defined
| [`htmx:onLoadError`](/events#htmx:onLoadError)  | triggered when an exception occurs during the onLoad handling in htmx
| [`htmx:oobAfterSwap`](/events#htmx:oobAfterSwap)  | triggered after an of band element as been swapped in
| [`htmx:oobBeforeSwap`](/events#htmx:oobBeforeSwap)  | triggered before an out of band element swap is done, allows you to configure the swap
| [`htmx:oobErrorNoTarget`](/events#htmx:oobErrorNoTarget)  | triggered when an out of band element does not have a matching ID in the current DOM
| [`htmx:prompt`](/events#htmx:prompt)  | triggered after a prompt is shown
| [`htmx:pushedIntoHistory`](/events#htmx:pushedIntoHistory)  | triggered after an url is pushed into history
| [`htmx:responseError`](/events#htmx:responseError)  | triggered when an HTTP response error (non-`200` or `300` response code) occurs
| [`htmx:sendError`](/events#htmx:sendError)  | triggered when a network error prevents an HTTP request from happening
| [`htmx:sseError`](/events#htmx:sseError)  | triggered when an error occurs with a SSE source
| [`htmx:swapError`](/events#htmx:swapError)  | triggered when an error occurs during the swap phase
| [`htmx:targetError`](/events#htmx:targetError)  | triggered when an invalid target is specified
| [`htmx:timeout`](/events#htmx:timeout)  | triggered when a request timeout occurs
| [`htmx:validation:validate`](/events#htmx:validation:validate)  | triggered before an element is validated
| [`htmx:validation:failed`](/events#htmx:validation:failed)  | triggered when an element fails validation
| [`htmx:validation:halted`](/events#htmx:validation:halted)  | triggered when a request is halted due to validation errors
| [`htmx:xhr:abort`](/events#htmx:xhr:abort)  | triggered when an ajax request aborts
| [`htmx:xhr:loadend`](/events#htmx:xhr:loadend)  | triggered when an ajax request ends
| [`htmx:xhr:loadstart`](/events#htmx:xhr:loadstart)  | triggered when an ajax request starts
| [`htmx:xhr:progress`](/events#htmx:xhr:progress)  | triggered periodically during an ajax request that supports progress events

</div>

## <a name="api"></a> [Javascript API Reference](#api)

<div class="info-table">

| Method | Description |
|-------|-------------|
| [`htmx.addClass()`](/api#addClass)  | Adds a class to the given element
| [`htmx.ajax()`](/api#ajax)  | Issues an htmx-style ajax request
| [`htmx.closest()`](/api#closest)  | Finds the closest parent to the given element matching the selector
| [`htmx.config`](/api#config)  | A property that holds the current htmx config object
| [`htmx.createEventSource`](/api#createEventSource)  | A property holding the function to create SSE EventSource objects for htmx
| [`htmx.createWebSocket`](/api#createWebSocket)  | A property holding the function to create WebSocket objects for htmx
| [`htmx.defineExtension()`](/api#defineExtension)  | Defines an htmx [extension](/extensions)
| [`htmx.find()`](/api#find)  | Finds a single element matching the selector
| [`htmx.findAll()` `htmx.findAll(elt, selector)`](/api#find)  | Finds all elements matching a given selector
| [`htmx.logAll()`](/api#logAll)  | Installs a logger that will log all htmx events
| [`htmx.logger`](/api#logger)  | A property set to the current logger (default is `null`)
| [`htmx.off()`](/api#off)  | Removes an event listener from the given element
| [`htmx.on()`](/api#on)  | Creates an event listener on the given element, returning it
| [`htmx.onLoad()`](/api#onLoad)  | Adds a callback handler for the `htmx:load` event
| [`htmx.parseInterval()`](/api#parseInterval)  | Parses an interval declaration into a millisecond value
| [`htmx.process()`](/api#process)  | Processes the given element and its children, hooking up any htmx behavior
| [`htmx.remove()`](/api#remove)  | Removes the given element
| [`htmx.removeClass()`](/api#removeClass)  | Removes a class from the given element
| [`htmx.removeExtension()`](/api#removeExtension)  | Removes an htmx [extension](/extensions)
| [`htmx.takeClass()`](/api#takeClass)  | Takes a class from other elements for the given element
| [`htmx.toggleClass()`](/api#toggleClass)  | Toggles a class from the given element
| [`htmx.trigger()`](/api#trigger)  | Triggers an event on an element
| [`htmx.values()`](/api#values)  | Returns the input values associated with the given element

</div>

