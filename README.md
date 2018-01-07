# todoapp

Implementation of Todo App on different platforms and in different languages.
The common feature of all implementations is data interoperability (you can take
the same file with your tasks and run it on another platform).

# file format

Each implementation uses the same format of file. All integers (more than one
byte long) are little-endian encoded.

File structure is an event log. Each event is stored as:

- event type (1 byte)
- event size (2 bytes)
- event content

There are 3 event types:

1. add todo - content is a todo title
2. delete todo - soft-delete todo - the content is a pointer of the adding event
3. complete todo - complete todo - the content is a pointer of the adding event
4. start - the time of starting the work on the todo - the content is a timestamp
 and pointer of adding event.
5. stop - the time of stopping the work - the content is a timestamp and pointer.

The timestamp is (YYYY-MM-DDTHH:MM) format.
The pointer is 4 bytes and can be interpreted as an ID of the todo item.
