# C++

https://qpid.apache.org/releases/qpid-proton-0.38.0/proton/cpp/api/annotated.html

## Move the TLS impl to use the new C TLS API

And rename the C++ interfaces from SSL to TLS.

## Mark the unsettled APIs settled

Or remove them.

~~~
codec
io
connection and connection_options
properties() on link options
drain(), draining(), return_credit(), and the messaging_handler methods
filter_map()
port() and container() on listener
connection wake and messaging_handler::on_connection_wake
~~~

## Move url.h out of the public headers

And also remove the proton::url mention in cpp/examples/tutorial.dox.

## Remove the deprecated failover_connections stuff

## Update the docs to reflect that C++11 is a required minimum

For example, container::schedule need not handle any pre-11
considerations.

## Should we drop the "returned" values on container?

For example, the one on container::connect().

And if we do this, remove the "returned" class.

## Remove the connect_config API?

I don't see why it should have one.

If we keep it, we should rename it to connection_config so it matches
its sibling names.

## Need to look at the types we're using for maps

~~~
connection::properties()       -> std::map<symbol, value>
source::filters()              -> filter_map (proton::map<symbol, value>
source::dynamic_properties()   -> dynamic_property_map
error_condition::properties()  -> proton::value
message::properties()          -> property_map (proton::map<std::string, scalar>)
message::message_annotations() -> annotation_map (proton::map<annotation_key, value>)
~~~

## Improve naming in listen_handler

~~~
on_open -> on_listener_open
on_accept -> on_listener_accept
on_error -> on_listener_error
on_close -> on_listener_close
~~~

## Renames

~~~
message::message_annotations to message::annotations
sasl::mech to sasl::mechanism
~~~
