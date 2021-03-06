.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.


All heartbeat messaging is done using |zeromq| and all messages between components are formatted as |json|. 

* A heartbeat message is sent by the |pushy| server to every managed node. This lets each of those nodes know that the |pushy| server is available. This heartbeat message is one-way; no acknowledgements are returned by the nodes. |zeromq| (and its PUBLISH / SUBSCRIBE pattern) is used for heartbeat messages sent by the |pushy| server. The frequency of this heartbeat message is configurable. 
* A heartbeat message is sent by a node to the |pushy| server. This lets the |pushy| server know which nodes are available. This heartbeat message is one-way; no acknowledgements are returned by the |pushy| server. If the |pushy| server is unavailable, a node will discontinue heartbeats until the |pushy| server heartbeat resumes. |zeromq| (and its DEALER / ROUTER pattern) is used for heartbeat messages sent by nodes.

A |pushy| job may not be completed if either the |pushy| server or a certain number of nodes are unavailable. (The number of nodes that may be unavailable is determined by the ``quorum`` setting when the request is made.)