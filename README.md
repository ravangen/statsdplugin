# Hosted Graphite statsd plugin

This is a plugin for [etsy's statsd](https://github.com/etsy/statsd) that sends your metric data to the [Hosted Graphite](http://www.hostedgraphite.com) service.

## Installation

Place **hostedgraphite.js** into the **backends/** directory of your **statsd** install.

## Configuration

Accepts same configuration options as [graphite](https://github.com/etsy/statsd/blob/v0.7.2/exampleConfig.js#L65).

```
hostedGraphite:
    legacyNamespace:  use the legacy namespace [default: true]
    globalPrefix:     global prefix to use for sending stats to graphite [default: "stats"]
    prefixCounter:    graphite prefix for counter metrics [default: "counters"]
    prefixTimer:      graphite prefix for timer metrics [default: "timers"]
    prefixGauge:      graphite prefix for gauge metrics [default: "gauges"]
    prefixSet:        graphite prefix for set metrics [default: "sets"]
    globalSuffix:     global suffix to use for sending stats to graphite [default: ""]
                      This is particularly useful for sending per host stats by
                      settings this value to: require('os').hostname().split('.')[0]
```

### Enabling the plugin

Add './backends/hostedgraphite' to the ```backends``` list.

```
backends: ['./backends/hostedgraphite']
```

### Setting the Hosted Graphite key

Set ```hostedGraphiteAPIKey``` to your key. This looks like a UUID and is available from your account details page on [hostedgraphite.com](hostedgraphite.com)

```
hostedGraphiteAPIKey: 'deadbeef-dead-beef-dead-beefdeadbeef'
```

## Example configuration

```
{
      port: 8125
   ,  backends: ['./backends/hostedgraphite']
   ,  hostedGraphiteAPIKey: 'deadbeef-dead-beef-dead-beefdeadbeef'
   ,  hostedGraphite: {
          legacyNamespace: false
      }
}
```