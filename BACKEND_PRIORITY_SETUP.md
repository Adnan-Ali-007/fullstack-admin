# Backend Priority Setup Guide

## Step 1: Install Dependencies
```bash
cd server
npm install
```

## Step 2: Environment Setup
Create `.env` file with:
```env
PORT=5001
MONGO_URL=mongodb://localhost:27017/admin-dashboard
NODE_ENV=development
```

## Step 3: Database Population (CRITICAL)
In `server/index.js`, uncomment these lines (lines 47-52):

```javascript
/* ONLY ADD DATA ONE TIME */
AffiliateStat.insertMany(dataAffiliateStat);
OverallStat.insertMany(dataOverallStat);
Product.insertMany(dataProduct);
ProductStat.insertMany(dataProductStat);
Transaction.insertMany(dataTransaction);
User.insertMany(dataUser);
```

## Step 4: Start Backend
```bash
npm run dev
```

## Step 5: Verify Data Population
After first successful run, **COMMENT OUT** the data insertion lines again:
```javascript
/* ONLY ADD DATA ONE TIME */
// AffiliateStat.insertMany(dataAffiliateStat);
// OverallStat.insertMany(dataOverallStat);
// Product.insertMany(dataProduct);
// ProductStat.insertMany(dataProductStat);
// Transaction.insertMany(dataTransaction);
// User.insertMany(dataUser);
```

## Step 6: Test API Endpoints
```bash
# Test user endpoint
curl http://localhost:5001/general/user/63701cc1f03239b7f700000e

# Test products endpoint
curl http://localhost:5001/client/products

# Test dashboard endpoint
curl http://localhost:5001/general/dashboard
```

## Key Backend Endpoints
- `GET /general/user/:id` - Get user by ID
- `GET /general/dashboard` - Dashboard statistics
- `GET /client/products` - All products with stats
- `GET /client/customers` - All customers
- `GET /client/transactions` - Paginated transactions
- `GET /client/geography` - Geographic user distribution
- `GET /sales/sales` - Sales analytics
- `GET /management/admins` - Admin users
- `GET /management/performance/:id` - User performance

## Database Collections Created
- users (admin and customer data)
- products (product catalog)
- productstats (product statistics)
- transactions (sales transactions)
- overallstats (aggregated statistics)
- affiliatestats (performance metrics)

## Important Notes
1. **MongoDB must be running** on port 27017
2. **Uncomment data insertion only ONCE** to avoid duplicates
3. **Comment out data insertion** after first successful run
4. Server runs on **http://localhost:5001**
5. All API endpoints are **CORS enabled** for frontend integration

## Troubleshooting
- If MongoDB connection fails, ensure MongoDB is running
- If data insertion fails, check MongoDB permissions
- If port 5001 is busy, change PORT in .env file