---
layout: default
title: SSL/TLS
nav_order: 1
parent: Transport
redirect_from: /docs/client_configuration.html
---

# SSL/TLS

SSL/TLS protocols allow the connection between two mediums (client-server) to be encrypted. Encryption lets you make sure that no third party is able to read the data or tamper with it.

The SSL/TLS configuration is the same for both protocols, and it comes in two flavors:

## Simple TLS config  

{% capture tab_content %}

Studio
===
![mqtt3-connection]({{ site.baseurl }}/images/3-connection-mqtt3.png)
====

Code
===

```xml
<mqtt:config name="MQTT5">
    <mqtt:mqtt5-connection host="test.mosquitto.org" port="8883">
        <mqtt:tls-configuration>
            <mqtt:simple-tls-config caCertificate="ca.crt" />
        </mqtt:tls-configuration>
    </mqtt:mqtt5-connection>
</mqtt:config>
```

{% endcapture %}
{% include tabs.html tab_group="module" %}

---

| Parameter | Description | Default value |
| ----------- | ----------- | ------------- |
| `caCertificate` | the path to the CA X509 certificate resource | - |

## Advanced TLS config  

{% capture tab_content %}

Studio
===
![mqtt3-connection]({{ site.baseurl }}/images/3-connection-mqtt3.png)
====

Code
===

```xml
<mqtt:config name="MQTT5">
    <mqtt:mqtt5-connection host="test.mosquitto.org" port="8883">
        <mqtt:tls-configuration>
            <mqtt:advanced-tls-config>
                <tls:context>
                    <tls:trust-store path="truststore.jks" type="jks" password="changeit" insecure="false"/>
                </tls:context>
            </mqtt:advanced-tls-config>
        </mqtt:tls-configuration>
    </mqtt:mqtt5-connection>
</mqtt:config>
```

{% endcapture %}
{% include tabs.html tab_group="module" %}

---

#### TLS trust store

| Parameter | Description | Default value |
| ----------- | ----------- | ------------- |
| `path` | The path to the truststore file or resource | - |
| `password` | The password for the truststore file | - |
| `type` | The type of the truststore | `JKS` |
| `insecure` | Disables verification of the server hostname in the server certificate | `false` |
