---
---



## Chat Arena 

### Chat with two models side-by-side and vote for which one is better!

https://chat.lmsys.org/



## notes on redis and postgres

So, adding contextual memory... So, for each message before the LLM is queried, a Redis cache is queried. for the top-k relevant quote-unquote memories. This will allow the addressing of topic changes in a conversation without the occurrence of catastrophic interference.


So, between Postgres and Redis, the major difference that I've noticed is that when I'm using Redis, I don't think about looking at it, whereas with Postgres, I feel compelled to load up something like pgmodeler to look at the tables. In terms of interacting with either one for Ruby, using the OMGEM makes it fairly trivial, whereas even with the SQLGEM interacting with the Postgres database, it does add another layer of complexity. So not only does the database require extensions to accommodate...well, I don't know, with the SQLGEM, it does sort of level that out. So with Redis acting as a caching mechanism, then the concern becomes data retention. The idea was to, for each document that is ingested, to create a JSON-L file. Anything LLM is a good example of this. This has the advantage over storing in a database for a couple of reasons. If the database should go offline for whatever reason, the documents can still be accessed in two ways. One, either just directly reading the document file itself, or making the JSON-L files available. That way, it cuts down on having to make SQL queries, where if you want to look up some information, instead of opening up a console, connecting to a database, making a query, you can open the JSON-L file, do a CTRL-F, or if you traverse to the JSON-L directory, use ripgrep, or find...


So, a persistent redis state can be exported or saved from time to time, so it's a cache, right? So, it should be available at least for the duration of the session. So, if it's a service, so it's running in the background as a daemon, when that service starts, if the loading mechanism is fast enough, it could just load the JSON-L files. So, if you make a query, you get a response, another query, another response, and these are all within the same context, at the end of the query session, if the feedback is determined to be positive, then that conversation gets stored in the cache. So, context add, or context create, give it a unique identifier, and then store the messages between, yeah, it'll be messages, user assistant. We'll get the embeddings first, then store the conversation with an identifier, the text. So, each, well, the entire conversation should be summarized first, and then once that's summarized, then each message segment can be considered a chunk. So, you have, you open up the application, and so you say, route all jack connections in the example session. So, somewhere stored is already system information, there also should be probably an index of all of the commands and their arguments, so when it goes to answer that query, when it invokes the cache, the cache will return all of the commands related to the query. If this has been queried in the past, then that cache response will also include that chat message with its identification, which, if that does return a previous chat message, then that entire prompt can be whittled down to just the logic of the current circumstance. Maybe you can even ask, has anything changed since the last time? And if the response is no, then it doesn't even need to query the LLM, it can just run the previously cached response.

```markdown
Here's a condensed and summarized ordered outline of the provided notes:

1. **Persistent Redis State and Caching**
   - Redis state export/saving for caching purposes.
   - Availability during a session due to caching.

2. **Service as a Daemon**
   - Running as a background daemon.
   - Quick JSON-L file loading on service start.

3. **Cache Handling for Conversations**
   - Positive feedback stores the conversation in the cache.
   - Context addition/creation with a unique identifier.

4. **Message Storage and Embeddings**
   - Storing conversation messages with embeddings.
   - Summarizing the entire conversation.

5. **Querying and Cache Response**
   - Retrieving commands related to a query from the cache.
   - Efficient handling based on past queries and cached responses.

6. **Efficient Application Use**
   - Utilizing system information and an index of commands.
   - Optimizing queries by leveraging cached responses effectively.
```