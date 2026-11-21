A keep-alive connection now automatically returns to the reusable
``IDLE`` state once a full request/response cycle finishes with an empty
receive buffer, so the next request can be sent without an explicit
:meth:`~h11.Connection.start_next_cycle` call. When buffered bytes remain
(for example a pipelined request), the connection still pauses and keeps
those bytes for the next cycle instead of treating them as the start of a
new request.
