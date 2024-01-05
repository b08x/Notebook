
## postgresql pgvector
#sequel #ruby #postgresql

[pgvector](https://github.com/pgvector/pgvector)

[pgvector-ruby#sequel](https://github.com/pgvector/pgvector-ruby#sequel)


```python
async def upsert(self, table: str, json: dict[str, Any]):
        """
        Takes in a list of documents and inserts them into the table.
        """
        with self.client.cursor() as cur:
            if not json.get("created_at"):s1 --> s2: A transition

                json["created_at"] = datetime.now()
            json["embedding"] = np.array(json["embedding"])
            cur.execute(
                f"INSERT INTO {table} (id, content, embedding, document_id, source, source_id, url, author, created_at) VALUES (%s, %s, %s, %s, %s, %s, %s, %s, %s) ON CONFLICT (id) DO UPDATE SET content = %s, embedding = %s, document_id = %s, source = %s, source_id = %s, url = %s, author = %s, created_at = %s",
                (
                    json["id"],
                    json["content"],
                    json["embedding"],
                    json["document_id"],
                    json["source"],
                    json["source_id"],
                    json["url"],
                    json["author"],
                    json["created_at"],
                    json["content"],
                    json["embedding"],
                    json["document_id"],
                    json["source"],
                    json["source_id"],
                    json["url"],
                    json["author"],
                    json["created_at"],
                ),
            )
            self.client.commit()

```
[souce](https://github.com/openai/chatgpt-retrieval-plugin/blob/main/datastore/providers/postgres_datastore.py)


Given a document from a user, try to extract the following metadata:

- source: string, one of {sources_string}
- url: string or don't specify
- created_at: string or don't specify
- author: string or don't specify

https://github.com/openai/chatgpt-retrieval-plugin/blob/main/services/file.py

So, for each document that's parsed, so, if it's, if, if, if, I suppose on input, if it's like, dash, dash, Ansible, and then point it to a folder, and then for each YAML file that, that, that, that is in the directory, parse it like the Ruby docs parser, and then
