[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19756058&assignment_repo_type=AssignmentRepo)
# Express.js RESTful API Assignment

This assignment focuses on building a RESTful API using Express.js, implementing proper routing, middleware, and error handling.

## Assignment Overview

You will:
1. Set up an Express.js server
2. Create RESTful API routes for a product resource
3. Implement custom middleware for logging, authentication, and validation
4. Add comprehensive error handling
5. Develop advanced features like filtering, pagination, and search

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Install dependencies:
   ```
   npm install
   ```
4. Run the server:
   ```
   npm start
   ```

## Files Included

- `Week2-Assignment.md`: Detailed assignment instructions
- `server.js`: Starter Express.js server file
- `.env.example`: Example environment variables file

## Requirements

- Node.js (v18 or higher)
- npm or yarn
- Postman, Insomnia, or curl for API testing

## API Endpoints

The API will have the following endpoints:

- `GET /api/products`: Get all products
- `GET /api/products/:id`: Get a specific product
- `POST /api/products`: Create a new product
- `PUT /api/products/:id`: Update a product
- `DELETE /api/products/:id`: Delete a product

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all the required API endpoints
2. Implement the middleware and error handling
3. Document your API in the README.md
4. Include examples of requests and responses

## Resources

- [Express.js Documentation](https://expressjs.com/)
- [RESTful API Design Best Practices](https://restfulapi.net/)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

mkdir products-api
cd products-api
npm init -y
npm install express morgan
// index.js
const express = require('express');
const app = express();
const port = 3000;

// Middleware to parse JSON bodies
app.use(express.json());

// Custom logging middleware
app.use(require('./middleware/logger'));

// Routes
const productsRouter = require('./routes/products');
app.use('/api/products', productsRouter);

// Global error handler
app.use(require('./middleware/errorHandler'));

app.listen(port, () => {
  console.log(`Server running on http://localhost:${port}`);
});
module.exports = (req, res, next) => {
  console.log(`${new Date().toISOString()} - ${req.method} ${req.originalUrl}`);
  module.exports = (req, res, next) => {
  const authHeader = req.headers['authorization'];
  if (authHeader && authHeader === 'Bearer mysecrettoken') {
    next();
  } else {
    res.status(401).json({ message: 'Unauthorized' });
    module.exports = (req, res, next) => {
  const { name, price } = req.body;
  if (typeof name !== 'string' || name.trim() === '') {
    return res.status(400).json({ message: 'Invalid or missing product name' });

    CREATE a new product
router.post('/', auth, validateProduct, (req, res, next) => {
  try {
    const newProduct = {
      id: nextId++,
      name: req.body.name,
      price: req.body.price
    };
    products.push(newProduct);
    res.status(201).json(newProduct);
  } catch (err) {
    next(err);
  }
});

// UPDATE a product
router.put('/:id', auth, validateProduct, (req, res, next) => {
  try {
    const product = products.find(p => p.id === parseInt(req.params.id));
    if (!product) return res.status(404).json({ message: 'Product not found' });
    product.name = req.body.name;
    product.price = req.body.price;
    res.json(product);
  } catch (err) {
    next(err);
  }
});

// DELETE a product
router.delete('/:id', auth, (req, res, next) => {
  try {
    const index = products.findIndex(p => p.id === parseInt(req.params.id));
    if (index === -1) return res.status(404).json({ message: 'Product not found' });
    products.splice(index, 1);
    res.status(204).end();
  } catch (err) {
    next(err);
  }
});

module.exports = router;
