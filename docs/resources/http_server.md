---
page_title: "thousandeyes_http_server Resource - terraform-provider-thousandeyes"
subcategory: ""
description: |-
---

# thousandeyes_http_server (Resource)

This resource allows you to create an HTTP server test. This test type measures the availability and performance of an HTTP service. For more information, see [HTTP Server Tests](https://docs.thousandeyes.com/product-documentation/internet-and-wan-monitoring/tests#http-server-test).

## Example Usage

```terraform
resource "thousandeyes_http_server" "example_http_server_test" {
  test_name      = "Example HTTP test set from Terraform provider"
  interval       = 120
  alerts_enabled = false

  url = "https://www.thousandeyes.com"

  agents {
    agent_id = 3 # Singapur
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `agents` (Block Set, Min: 1) The list of ThousandEyes agents to use. (see [below for nested schema](#nestedblock--agents))
- `interval` (Number) The interval to run the test on, in seconds.
- `test_name` (String) The name of the test.
- `url` (String) The target URL for the test.

### Optional

- `alert_rules` (Block Set) Gets the ruleId from the /alert-rules endpoint. If alertsEnabled is set to 'true' and alertRules is not included in a creation/update query, the applicable defaults will be used. (see [below for nested schema](#nestedblock--alert_rules))
- `alerts_enabled` (Boolean) Set to 'true' to enable alerts, or 'false' to disable alerts. The default value is 'true'.
- `auth_type` (String) [NONE, BASIC, NTLM, KERBEROS] The HTTP authentication type. Defaults to NONE.
- `bandwidth_measurements` (Boolean) Set to 1 to measure bandwidth. This only applies to Enterprise Agents assigned to the test, and requires that networkMeasurements is set. Defaults to 'false'.
- `bgp_measurements` (Boolean) Enable BGP measurements. Set to true for enabled, false for disabled.
- `bgp_monitors` (Block List) The array of BGP monitor object IDs. The monitorIDs can be sourced from the /bgp-monitors endpoint. (see [below for nested schema](#nestedblock--bgp_monitors))
- `client_certificate` (String) String representation (containing newline characters) of the client certificate, if used.
- `content_regex` (String) Verify content using a regular expression. This field does not require escaping.
- `custom_headers` (Map of String) The custom headers.
- `description` (String) A description of the alert rule. Defaults to an empty string.
- `desired_status_code` (String) The valid HTTP response code you’re interested in retrieving.
- `dns_override` (String) The IP address to use for DNS override.
- `download_limit` (Number) Specify the maximum number of bytes to download from the target object.
- `enabled` (Boolean) Enables or disables the test.
- `follow_redirects` (Boolean) Follow HTTP/301 or HTTP/302 redirect directives. Defaults to 'true'.
- `groups` (Block List) The array of label objects. (see [below for nested schema](#nestedblock--groups))
- `headers` (List of String) ["header: value", "header2: value"] The array of header strings.
- `http_target_time` (Number) The target time for HTTP server completion, specified in milliseconds.
- `http_time_limit` (Number) The target time for HTTP server limits, specified in seconds.
- `http_version` (Number) Set to 2 for the default HTTP version (prefer HTTP/2), or 1 for HTTP/1.1 only.
- `mtu_measurements` (Boolean) Measure MTU sizes on the network from agents to the target.
- `network_measurements` (Boolean) Set to 'true' to enable network measurements.
- `num_path_traces` (Number) The number of path traces.
- `password` (String) The password to be used to authenticate with the destination server.
- `path_trace_mode` (String) [classic or inSession] Choose 'inSession' to perform the path trace within a TCP session. Default value is 'classic'.
- `post_body` (String) The POST body content. No escaping is required. If the post body is set to something other than empty, the requestMethod will be set to POST.
- `probe_mode` (String) [AUTO, SACk, or SYN] The probe mode used by end-to-end network tests. This is only valid if the protocol is set to TCP. The default value is AUTO.
- `protocol` (String) The protocol used by dependent network tests (end-to-end, path trace, PMTUD). Default value is TCP.
- `shared_with_accounts` (Block List) [“serverName”: “fqdn of server”] The array of DNS Server objects. (see [below for nested schema](#nestedblock--shared_with_accounts))
- `ssl_version_id` (Number) Defines the SSL version. 0 for auto, 3 for SSLv3, 4 for TLS v1.0, 5 for TLS v1.1, 6 for TLS v1.2.
- `use_ntlm` (Boolean) Enable to use basic authentication. Only include this field if you are using authentication. Requires the username and password to be set if enabled.
- `user_agent` (String) The user-agent string to be provided during the test.
- `username` (String) The username to be used to authenticate with the destination server.
- `verify_certificate` (Boolean) Set whether to ignore certificate errors. Set to 'false' to ignore certificate errors. The default value is 'true'.

### Read-Only

- `api_links` (List of Object) Self links to the endpoint to pull test metadata, and data links to the endpoint for test data. Read-only, and shows rel and href elements. (see [below for nested schema](#nestedatt--api_links))
- `created_by` (String) Created by user.
- `created_date` (String) The date of creation.
- `id` (String) The ID of this resource.
- `live_share` (Boolean) Set to 'true' for a test shared with your account group, or to 'false' for a normal test.
- `modified_by` (String) Last modified by this user.
- `modified_date` (String) The date the test was last modified. Shown in UTC.
- `saved_event` (Boolean) Set to 'true' for a saved event, or to 'false' for a normal test.
- `ssl_version` (String) Reflects the verbose ssl protocol version used by a test.
- `test_id` (Number) The unique ID of the test.
- `type` (String) The type of test.

<a id="nestedblock--agents"></a>
### Nested Schema for `agents`

Optional:

- `agent_id` (Number) The unique ID for the ThousandEyes agent.
- `agent_name` (String) The name of the agent.
- `agent_state` (String) Defines whether the agent's status is online, offline, or disabled.
- `cluster_members` (Block List) Detailed information about each cluster member, shown as an array. This field is not shown for Enterprise Agents in standalone mode, or for Cloud Agents. (see [below for nested schema](#nestedblock--agents--cluster_members))
- `country_id` (String) The two-digit ISO country code of the agent.
- `created_date` (String) The date the agent was created. Expressed in UTC (yyyy-MM-dd hh:mm:ss).
- `enabled` (Boolean) Shows whether the agent is enabled or disabled.
- `error_details` (Block List) If one or more errors present in the agent, the error details are shown for each as an array. (see [below for nested schema](#nestedblock--agents--error_details))
- `groups` (Block List) An array of label objects. (see [below for nested schema](#nestedblock--agents--groups))
- `hostname` (String) Fully qualified domain name of the agent.
- `ip_addresses` (List of String) An array of the ipAddress entries.
- `ipv6_policy` (String) [FORCE_IPV4, PREFER_IPV6 or FORCE_IPV6] The IP version policy.
- `keep_browser_cache` (Boolean) Defines whether the browser cache should be kept. Either 1 for enabled or 0 for disabled.
- `last_seen` (String) The last time the agent connected with ThousandEyes. Shown in UTC (yyyy-MM-dd hh:mm:ss).
- `location` (String) The location of the agent.
- `network` (String) The name of the autonomous system in which the agent is found.
- `prefix` (String) The network prefix, expressed in CIDR format.
- `target_for_tests` (String) The target IP address or domain name representing the test destination when the agent is acting as a test target in an agent-to-agent test.
- `utilization` (Number) Shows the overall utilization percentage.
- `verify_ssl_certificate` (Boolean) Shows whether the SSL certificate needs to be verified. 1 for enabled and 0 for disabled.

Read-Only:

- `agent_type` (String) The type of ThousandEyes agent. Default value is enterprise.

<a id="nestedblock--agents--cluster_members"></a>
### Nested Schema for `agents.cluster_members`

Optional:

- `agent_state` (String) Defines whether the agent's status is online, offline, or disabled.
- `ip_addresses` (List of String) The array of ipAddress entries.
- `last_seen` (String) The last time the agent connected with ThousandEyes. Uses UTC (yyyy-MM-dd hh:mm:ss).
- `member_id` (Number) The unique ID of the cluster member.
- `name` (String) The name of the cluster member.
- `network` (String) The name of the autonomous system in which the Enterprise Agent is found (Enterprise Agents only).
- `prefix` (String) The network prefix, in CIDR format (Enterprise Agents only).
- `public_ip_addresses` (List of String) The array of public ipAddress entries.
- `target_for_tests` (String) The target IP address or domain name. Represents the test's destination when the agent is acting as a test target in an agent-to-agent test.
- `utilization` (Number) Shows the overall utilization percentage of a cluster member.


<a id="nestedblock--agents--error_details"></a>
### Nested Schema for `agents.error_details`

Optional:

- `code` (String) [AGENT_VERSION_OUTDATED, APPLIANCE_VERSION_OUTDATED, BROWSERBOT_VERSION_OUTDATED, CLOCK_OFFSET, NAT_TRAVERSAL_ERROR, OS_END_OF_INSTALLATION_SUPPORT, OS_END_OF_SUPPORT, or OS_END_OF_LIFE] The error code.
- `description` (String) A detailed explanation of the error code.


<a id="nestedblock--agents--groups"></a>
### Nested Schema for `agents.groups`

Optional:

- `builtin` (Number) Shows whether you are using built-in (1) labels or user-created (2) labels. Built-in labels are read-only.
- `group_id` (Number) The unique ID of the label. This number is negative for built-in labels. Query the /groups/{id} endpoint to see a list of agents/tests with this label.
- `name` (String) The name of the label.
- `type` (String) [tests, agents, endpoint_tests or endpoint_agents] The type of label.



<a id="nestedblock--alert_rules"></a>
### Nested Schema for `alert_rules`

Optional:

- `rule_id` (Number) The unique ID of the alert rule.


<a id="nestedblock--bgp_monitors"></a>
### Nested Schema for `bgp_monitors`

Required:

- `monitor_id` (Number) The unique ID of the BGP monitor.

Optional:

- `ip_address` (String) The IP address of the BGP monitor.
- `monitor_name` (String) The name of the BGP monitor.
- `monitor_type` (String) [Public or Private] Shows the type of BGP monitor.
- `network` (String) The name of the autonomous system in which the BGP monitor is found.


<a id="nestedblock--groups"></a>
### Nested Schema for `groups`

Required:

- `group_id` (Number) The unique ID of the label

Optional:

- `agents` (Block List) Define the ThousandEyes agents to use. (see [below for nested schema](#nestedblock--groups--agents))
- `name` (String) The name of the label.
- `tests` (Block List) The list of tests. (see [below for nested schema](#nestedblock--groups--tests))
- `type` (String) [tests, agents, endpoint_tests, or endpoint_agents] The type of label.

Read-Only:

- `builtin` (Boolean) Shows whether you are using built-in (true) labels or user-created (false) labels. Built-in labels are read-only.

<a id="nestedblock--groups--agents"></a>
### Nested Schema for `groups.agents`

Optional:

- `agent_id` (Number) The unique ThousandEyes agent ID.


<a id="nestedblock--groups--tests"></a>
### Nested Schema for `groups.tests`

Optional:

- `test_id` (Number) The unique ID of the test.



<a id="nestedblock--shared_with_accounts"></a>
### Nested Schema for `shared_with_accounts`

Required:

- `aid` (Number) The account group ID.

Read-Only:

- `name` (String) The name of account.


<a id="nestedatt--api_links"></a>
### Nested Schema for `api_links`

Read-Only:

- `href` (String)
- `rel` (String)


