# Lightstreamer - Market Depth Demo - HTML Client

The *Market Depth Demo* is a very simple market depth application based on Lightstreamer for its real-time communication needs.<br>

This project includes a web client front-end for the demo.
The server-side part of this demo, the Metadata and Data Adapters, is covered in this project: [Lightstreamer - Market Depth Demo - Java Adapter](https://github.com/Weswit/Lightstreamer-example-MarketDepth-adapter-java).

## Live Demo

[![screenshot](screenshot.png)](http://demos.lightstreamer.com/MarketDepthDemo)

###[![](http://demos.lightstreamer.com/site/img/play.png) View live demo](http://demos.lightstreamer.com/MarketDepthDemo)

## Details

Market depth is an electronic list of buy and sell orders, organized by price level and updated to reflect real-time market activity. 
Market depth data are also known as Level II, Depth Of Market (DOM), and the order book.<br>
<br>
Lightstreamer has semi-native support for market depth, which can be managed very easily via COMMAND mode subscriptions. Basically, the bid and ask lists for an instrument will be two items subscribed to in COMMAND mode.<br>
You will be able to add, update, and remove rows, where each row is identified by a key, which is the price. Lightstreamer will take care of aggregating updates to market depth in the most optimized way, based on bandwidth and frequency constraints.<br>
This way, you will be able to manage full market depths even on unreliable networks and also benefit from update resampling with conflation, if needed.<br>

The demo is based on an adapter that simulates the generation of random orders and any contracts in case of matching. Furthermore you can add orders at your convenience through the basic input form.<br>

The demo includes the following client-side functionalities:
* A [Subscription](http://www.lightstreamer.com/docs/client_javascript_uni_api/Subscription.html) containing 1 item, subscribed to in `MERGE` mode feeding a [StaticGrid](http://www.lightstreamer.com/docs/client_javascript_uni_api/StaticGrid.html) (showing summary data for the stock).
* Two [Subscription](http://www.lightstreamer.com/docs/client_javascript_uni_api/Subscription.html)s containing 1 item each, subscribed to in `COMMAND` mode feeding two [DynaGrid](http://www.lightstreamer.com/docs/client_javascript_uni_api/DynaGrid.html)s (showing the bid and ask lists).
* The orders are sent to the adapter through the Lightstreamer Server using the [LightstreamerClient.sendMessage](http://www.lightstreamer.com/docs/client_javascript_uni_api/LightstreamerClient.html#sendMessage) utility.

## Install

If you want to install a version of this demo pointing to your local Lightstreamer Server, follow these steps:
* As prerequisite, the [Lightstreamer - Market Depth Demo - Java Adapter](https://github.com/Weswit/Lightstreamer-example-MarketDepth-adapter-java) has to be deployed on your local Lightstreamer Server instance. Please check out that project and follow the installation instructions provided with it.
* Download this project.
* Get the `lightstreamer.js` file from the [latest Lightstreamer distribution](http://www.lightstreamer.com/download) and put it in the `src/js` folder.
Alternatively, you can build a `lightstreamer.js` file from the [online generator](http://www.lightstreamer.com/distros/Lightstreamer_Allegro-Presto-Vivace_6_0_20150213/Lightstreamer/DOCS-SDKs/sdk_client_javascript/tools/generator.html). In that case, be sure to include the LightstreamerClient, Subscription, StaticGrid, DynaGrid, and StatusWidget modules and to use the "Use AMD" version.
* Get the `require.js` file form [requirejs.org](http://requirejs.org/docs/download.html) and put it in the `src/js` folder.
* Deploy this demo on the Lightstreamer Server (used as Web server) or in any external Web Server. In the former case, please create the folders `<LS_HOME>/pages/MarketDepthDemo` and copy here the contents of the `/src` folder of this project.
The client demo configuration assumes that Lightstreamer Server, Lightstreamer Adapters, and this client are launched on the same machine. If you need to target a different Lightstreamer server, please search in `js/lsClient.js` this line:<BR/> 
```
var lsClient = new LightstreamerClient(protocolToUse+"//localhost:"+portToUse,"MARKETDEPTH");
```
and change it accordingly.
* Open your browser and point it to: [http://localhost:8080/MarketDepthDemo/](http://localhost:8080/MarketDepthDemo/)

## See Also

### Lightstreamer Adapters Needed by This Client

* [Lightstreamer - Basic Market Depth Demo - Java Adapter](https://github.com/Weswit/Lightstreamer-example-MarketDepth-adapter-java)

## Lightstreamer Compatibility Notes

* Compatible with Lightstreamer JavaScript Client library version 6.2 or newer.
