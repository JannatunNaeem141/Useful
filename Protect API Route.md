# Protect API Route
In my ReactJS project, there are two files. One is for the client side and another for the server side. 
The client-side runs on “http://localhost:3000”. And server side runs on “http://localhost:5000”. On the server side, there are so many APIs that are made with ExpressJS and so many.

But the problem is, when anybody browses this api-link (“http://localhost:5000/blogs”), they can access the JSON format of my blog data. It is not a professional work as there is no security of my data. That should be solved.

And the solution idea is, If I fixed the api route for a specific domain, that could be a solution. There can be two verity One is for one domain and another is for multiple domains.

## Technologies:
- ReactJS/NextJS
- ExpressJS

## Single Domain
```jsx
  const checkReferer = (req, res, next) => {
    const referer = req.get("Referer");
    if (!referer || !referer.toLowerCase().includes(`http://localhost:3000`)) {
      return res.status(403).json({ message: "Access forbidden" });
    }
    next();
  };
```

#### Use the checkReferer like that:
```jsx
  // Get blogs
  app.get("/blogs", checkReferer, (req, res) => {
    db.query("SELECT * FROM blogs", (err, result) => {
      if (err) {
        console.log(err);
      } else {
        res.send(result);
      }
    });
  });
```

## Multiple Domain
#### This will use the “cors”. (Recommended to use this method)
```jsx
  const cors = require("cors");
  app.use(cors());
  
  const allowedOrigins = [
    "http://xyz.net",
    "https://abc.net",
    "http://localhost:3000",
    // Add more allowed origins here
  ];
  
  const corsOptions = {
    origin: (origin, callback) => {
      if (allowedOrigins.includes(origin)) {
        callback(null, true);
      } else {
        callback('Access Denied');
      }
    }
  };
  
  app.use(cors(corsOptions));
```
#### ( “This method will not need to use in any api” )

