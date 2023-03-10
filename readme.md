## ax-supabase (digitalocean functions)

store the webhook from AX in supabase

this demo is deployed on DigitalOcean Functions

blog post to this repository: <https://madflex.de/digitalocean-functions/>


### setup

Create a table in supabase named "generated" and add the following fields (keep `id` and `created_at`):
```
document_id: uuid
uid: text
text: text
text_modified: timestamp without time zone
collection_id: int8
collection_name: text
language: varchar
html: text
html_axite: text
```

Copy ``project.yml.template`` to ``project.yml`` and set the environment variables:
```
SUPABASE_URL=my-url-to-my-awesome-supabase-instance
SUPABASE_KEY=my-supa-dupa-secret-supabase-api-key
```
and the webhook secret from AX:
```
AX_WEBHOOK_SECRET=copy-from-collection-settings-and-set-your-url-there-too
```

The function needs 512MB memory instead of the 256MB default! - This can be set in the DigitalOcean Functions UI for this function.


### deploy

```
doctl serverless deploy ax-do-supabase --remote-build
```


### development

Deploy and look at the logs.
