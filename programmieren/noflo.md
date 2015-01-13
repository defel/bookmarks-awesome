# Noflo

## Projects

- noflo
    - [github.com/noflo](https://github.com/noflo) - Flow-Based Programming for JavaScript
    - [github.com/noflo/noflo-ui](https://github.com/noflo/noflo-ui) - NoFlo Development Environment
    - [github.com/noflo/noflo-nodejs](https://github.com/noflo/noflo-nodejs) - Node.js runtime environment for NoFlo UI
    - [github.com/noflo/fbp](https://github.com/noflo/fbp) - FBP flow definition language parser
    - [FBP Network Protocol](http://noflojs.org/documentation/protocol/)
- components
    - [github.com/djdeath/noflo-express](https://github.com/djdeath/noflo-express) - NoFlo components for the express web framework
    - [github.com/noflo/noflo-couchdb](https://github.com/noflo/noflo-couchdb) - CouchDB components for NoFlo
    - [github.com/djdeath/noflo-mongoose](https://github.com/djdeath/noflo-mongoose) - NoFlo components for the mongoose framework
    - [github.com/noflo/noflo-strings](https://github.com/noflo/noflo-strings) - String Utilities for NoFlo
    - [github.com/trustmaster/noflo-xpress](https://github.com/trustmaster/noflo-xpress) - High-level Express.js components for NoFlo



## Commands


> list all available noflo components
```bash
./node_modules/.bin/noflo list .
```

---

> run a noflo graph with debug output
```bash
./node_modules/.bin/noflo --debug graphs/server.fbp
```

---

## Documentation

### Components

A component is the main ingredient of flow-based programming. Component is a CommonJS module providing a set of input and output port handlers. These ports are used for connecting components to each other.

NoFlo processes (the boxes of a flow graph) are instances of a component, with the graph controlling connections between ports of components.

#### Structure of a component

Functionality a component provides:

- List of inports (named inbound ports)
- List of outports (named outbound ports)
- Handler for component initialization that accepts configuration
- Handler for connections for each inport
- Minimal component written in NoFlo would look like the following:

```js
noflo = require "noflo"

exports.getComponent = ->
  component = new noflo.Component
  component.description = "This component receives data on a single input
  port and sends the same data out to the output port"

  # Register ports and event handlers
  component.inPorts.add 'in', datatype: 'all', (event, payload) ->
    switch event
      when 'data'
        # Forward data when we receive it.
        # Note: send() will connect automatically if needed
        component.outPorts.out.send data
      when 'disconnect'
        # Disconnect output port when input port disconnects
        component.outPorts.out.disconnect()
  component.outPorts.add 'out', datatype: 'all'

  component # Return new instance
```

( via http://noflojs.org/documentation/components/ )

### FBP

The *fbp* library provides a parser for the [FBP domain-specific language](http://noflojs.org/documentation/fbp/) used for defining graphs for flowbased programming environments like [NoFlo](http://noflojs.org).


FBP is a Domain-Specific Language (DSL) for easy graph definition. The syntax is the following:

* `'somedata' -> PORT Process(Component)` sends initial data _somedata_ to port _PORT_ of process _Process_ that runs component _Component_
* `A(Component1) X -> Y B(Component2)` sets up a connection between port _X_ of process _A_ that runs component _Component1_ and port _Y_ of process _B_ that runs component _Component2_

You can connect multiple components and ports together on one line, and separate connection definitions with a newline or a comma (`,`).

Components only have to be specified the first time you mention a new process. Afterwards, simply append empty parentheses (`()`) after the process name.

Example:

```fbp
'somefile.txt' -> SOURCE Read(ReadFile) OUT -> IN Split(SplitStr)
Split() OUT -> IN Count(Counter) COUNT -> IN Display(Output)
Read() ERROR -> IN Display()
```

The syntax also supports blank lines and comments. Comments start with the `#` character.

Example with the same graph than above :

```fbp
# Read the content of "somefile.txt" and split it by line
'somefile.txt' -> SOURCE Read(ReadFile) OUT -> IN Split(SplitStr)

# Count the lines and display the result
Split() OUT -> IN Count(Counter) COUNT -> IN Display(Output)

# The read errors are also displayed
Read() ERROR -> IN Display()
```

( via https://github.com/noflo/fbp )

### Runtimes

All Compontents get executed within a so called Runtime Environment. There are different Runtimes to run the components in Browser, at the Server or on a MicroController.

#### Nodejs Runtime

In addition to being able to manage and run client-side NoFlo flows, the NoFlo UI is also able to run server-side NoFlo code (and indeed anything else [compatible with the API](#supporting-other-fbp-systems)). For NoFlo flows running on Node.js, you need to install and run [noflo-nodejs](https://github.com/noflo/noflo-nodejs).


> setup a Nodejs Runtime:
```bash
mkdir my-project
cd my-project
npm init
npm install noflo --save
npm install noflo-nodejs --save
```

#### Browser Runtime

The HTML runtime of NoFlo utilizes a custom [Component.io](http://component.io/) build of NoFlo that includes most of the common NoFlo [component libraries](http://noflojs.org/library/) that work with the browser. If you need to add new libraries, edit the `preview/component.json` file and rebuild.

#### Other Runtimes

Even though the UI itself is built with NoFlo, it isn't talking directly with that for running and building graphs. Instead, it is utilizing the [FBP Network Protocol](http://noflojs.org/documentation/protocol/) which enables it to talk to any compatible FBP system.

If you want to integrate the UI with a new environment you need to provide some transport layer (for example, WebSockets) that can talk the protocol, and then implement [runtime access](https://github.com/noflo/noflo-runtime) for that.
