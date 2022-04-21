## Installation

- Download and place the file(s) in a directory called AJAXPoll in your extensions/ folder.
- Add the following code at the bottom of your LocalSettings.php:

`wfLoadExtension( 'AJAXPoll' );`

- Run the update script which will automatically create the necessary database tables that this extension needs. Configure at your convenience.
- Done – Navigate to Special:Version on your wiki to verify that the extension is successfully installed.


## Configuration
```
# if you want to restrict the poll
# use the following code lines after calling the AJAXPoll extension
# to restrict to user group (example)

# The 'ajaxpoll-view-results-before-vote' group permission allows the specified
# group members to view poll results even without having voted
# but only if the high-level group permission 'ajaxpoll-vote' allows to view
# results in general.
#
# This 'ajaxpoll-view-results-before-vote' can be overwritten with the specific
# per-poll setting "show-results-before-voting" which takes precedence over the
# group permission.
#
# permission 'ajaxpoll-view-results' >>
# >> per-poll setting "show-results-before-voting" (if present)
# >> permission 'ajaxpoll-view-results-before-vote'

# anons
# default: anons cannot vote and will never see results
$wgGroupPermissions['*']['ajaxpoll-vote'] = false;
$wgGroupPermissions['*']['ajaxpoll-view-results'] = false;
$wgGroupPermissions['*']['ajaxpoll-view-results-before-vote'] = false;

# users
# default: users can vote and can see poll results - when they have voted
$wgGroupPermissions['user']['ajaxpoll-vote'] = true;
$wgGroupPermissions['user']['ajaxpoll-view-results'] = true;
```

If you want to disable the automatic tracking category then set the text of system message "MediaWiki:Ajaxpoll-tracking-category" in your wiki to "-" (minus). 

## Usage 
### Syntax
```
<poll>
id = uniqueid
poll=Question
option=Choice 1
option=Choice 2
option=Choice 3
option=Choice 4
</poll>
```
### Templates

To use inside a template and pass parameters, use parser functions etc., use the `{{#tag: function:`

```
{{#tag:poll|
id={{PAGEID}}
poll=Question
option=Choice 1
option=Choice 2
}}
```

you can allow or deny the result-viewing before voting per-poll by adding the show-results-before-voting parameter in the opening tag:

```
<poll show-results-before-voting>
<poll show-results-before-voting=1>
<poll show-results-before-voting=0>
```