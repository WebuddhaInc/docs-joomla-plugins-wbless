# Configuration

From the Joomla plugin manager, open the wbLess plugin to expose the configuration options.

## Watch Paths

These are paths that are examined for less files.  The watch path you specific will also scan all sub-folders.  You may use the `{$template}` variable key that will be supplanted with the currently template during runtime.

*Default: /templates/{$template}/less*

## Trigger Domains

These are domain hosts that can be used to limit when the plugin runs.  This can be used to isolate requests to development environments.

*Example: sandbox.website.com*

## Compress Output

This flag will enable CSS output compression.

## Watch Minimum Dependency

This flag will the compiler to any wildcard `*` rules when a rule specifically targets a LESS file.  By default both wildcard and file specific rules will be combined when processing a LESS file.

## Trigger Event

This flag will specify for which event during Joomla runtime will the plugin execute.

*Default: onAfterDispatch*

## Process Scope

This flag will specify whether the plugin will execute for requests to the Administrative, Site, or both interfaces.

*Default: All*

## Monitor Class

An optional less compiler may be specific that would be used rather than the internal processing.  The monitor that is included with this plugin is a mirror of the standalone LESS Monitor class by Webuddha.  Check out the standalone compiler Github for more details: [https://github.com/WebuddhaInc/LessMonitor](https://github.com/WebuddhaInc/LessMonitor)

