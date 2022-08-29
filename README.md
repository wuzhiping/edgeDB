# EdgeDB
https://www.edgedb.com/

# https://github.com/edgedb/edgedb
<pre>
version: "3"
services:
  edgedb:
    image: edgedb/edgedb
    environment:
      EDGEDB_SERVER_UID: edgedb
      EDGEDB_SERVER_PASSWORD: P@ssw0rd
      EDGEDB_SERVER_SECURITY: insecure_dev_mode
      #EDGEDB_SERVER_TLS_CERT_MODE: generate_self_signed
      EDGEDB_SERVER_ADMIN_UI: enabled
      #EDGEDB_SERVER_BACKEND_DSN: postgres://axelor:axelor@postgredb:5432/axelor
    volumes:
      - "./config:/.config/edgedb"
      - "./dbschema:/dbschema"
      - "./data:/var/lib/edgedb/data"
    ports:
      - "5656:5656"
    stdin_open: true
    tty: true

</pre>

# https://github.com/edgedb/edgedb-js
<pre>
process.env.EDGEDB_CLIENT_SECURITY = "insecure_dev_mode";
const edgedb = require("edgedb");

const client = edgedb.createClient( {dsn: "edgedb://edgedb:100861@localhost:5656/edgedb" } );

client.querySingle(`select uuid_generate_v1mc();`)
      .then((data)=>{ console.dir(data); });

</pre>
