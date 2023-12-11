# Protect API Route
In my ReactJS project, there are two files. One is for the client side and another for the server side. 
The client-side runs on “http://localhost:3000”. And server side runs on “http://localhost:5000”. On the server side, there are so many APIs that are made with ExpressJS and so many.

But the problem is, when anybody browses this api-link (“http://localhost:5000/blogs”), they can access the JSON format of my blog data. It is not a professional work as there is no security of my data. That should be solved.

And the solution idea is, If I fixed the api route for a specific domain, that can be a solution. There can be two verity One is for one domain and another is for multiple domains.





