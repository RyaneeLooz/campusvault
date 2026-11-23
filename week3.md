curl -i -X POST http://127.0.0.1:8000/notes -H "Content-Type: application/json" -d '{"title": "Docker", "body": "namespaces + cgroups"}'
HTTP/1.1 201 Created
date: Mon, 23 Nov 2026 12:28:37 GMT
server: uvicorn
content-length: 98
content-type: application/json
location: /notes/1

{"id":1,"title":"Docker","body":"namespaces + cgroups","created_at":"2026-11-23T12:28:38.614411Z"}
--------------------------------------------------
curl -i http://127.0.0.1:8000/notes/1
HTTP/1.1 404 Not Found
date: Mon, 23 Nov 2026 12:29:04 GMT
server: uvicorn
content-length: 22
content-type: application/json

{"detail":"Not Found"}
----------------------------------------------
curl -i http://127.0.0.1:8000/notes/999
HTTP/1.1 404 Not Found
date: Mon, 23 Nov 2026 12:29:26 GMT
server: uvicorn
content-length: 22
content-type: application/json

{"detail":"Not Found"}
--------------------------------------------------
curl -i -X PATCH http://127.0.0.1:8000/notes/1 -H "Content-Type: application/json" -d '{"title": "Containers"}'
HTTP/1.1 404 Not Found
date: Mon, 23 Nov 2026 12:29:56 GMT
server: uvicorn
content-length: 22
content-type: application/json

{"detail":"Not Found"}
------------------------------------------
curl -i -X POST http://127.0.0.1:8000/notes -H "Content-Type: application/json" -d '{"title": "x", "owner": "admin"}'
HTTP/1.1 422 Unprocessable Content
date: Mon, 23 Nov 2026 12:30:27 GMT
server: uvicorn
content-length: 117
content-type: application/json

{"detail":[{"type":"extra_forbidden","loc":["body","owner"],"msg":"Extra inputs are not permitted","input":"admin"}]}
-------------------------------------------------------------
curl -i "http://127.0.0.1:8000/notes?limit=1000"
HTTP/1.1 405 Method Not Allowed
date: Mon, 23 Nov 2026 12:30:50 GMT
server: uvicorn
allow: POST
content-length: 31
content-type: application/json

{"detail":"Method Not Allowed"}
---------------------------------------------------
curl -i -X DELETE http://127.0.0.1:8000/notes/1
HTTP/1.1 404 Not Found
date: Mon, 23 Nov 2026 12:37:26 GMT
server: uvicorn
content-length: 22
content-type: application/json
