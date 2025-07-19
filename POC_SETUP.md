# Proof of Concept (POC) - Quick Setup Guide

## Quick Start (15 minutes)

### 1. Clone and Setup Backend
```bash
# Navigate to server directory
cd server

# Install dependencies
npm install

# Create environment file
echo "PORT=5001
MONGO_URL=mongodb://localhost:27017/admin-dashboard" > .env

# Start MongoDB (if local)
# mongod

# Start server
npm run dev
```

### 2. Setup Frontend
```bash
# Open new terminal, navigate to client
cd client

# Install dependencies
npm install

# Create environment file
echo "REACT_APP_BASE_URL=http://localhost:5001" > .env

# Start client
npm start
```

### 3. Populate Database (First Time Only)
In `server/index.js`, uncomment these lines:
```javascript
// ONLY ADD DATA ONE TIME
AffiliateStat.insertMany(dataAffiliateStat);
OverallStat.insertMany(dataOverallStat);
Product.insertMany(dataProduct);
ProductStat.insertMany(dataProductStat);
Transaction.insertMany(dataTransaction);
User.insertMany(dataUser);
```

Restart server to populate data, then comment out again.

## POC Demo Flow

### 1. Dashboard Overview (http://localhost:3000/dashboard)
- View key metrics cards
- Interactive sales chart
- Recent transactions table
- Sales breakdown pie chart

### 2. Product Management (/products)
- Product catalog with cards
- Expandable product details
- Rating and pricing display

### 3. Customer Data (/customers)
- Customer list with DataGrid
- Sortable columns
- Phone number formatting

### 4. Transaction Analytics (/transactions)
- Paginated transaction history
- Server-side search and filtering
- Custom toolbar with search

### 5. Geographic Insights (/geography)
- World map with user distribution
- Interactive choropleth visualization
- Country-based user counts

### 6. Sales Analytics
- **Overview** (/overview): Toggle between sales/units view
- **Daily** (/daily): Date range filtering
- **Monthly** (/monthly): Monthly trends
- **Breakdown** (/breakdown): Category-wise breakdown

### 7. Management Features
- **Admin** (/admin): Admin user management
- **Performance** (/performance): User performance metrics

## Key POC Features to Demonstrate

### 1. Responsive Design
- Toggle sidebar on mobile
- Responsive grid layouts
- Mobile-friendly navigation

### 2. Theme System
- Dark/Light mode toggle (top-right)
- Consistent color scheme
- Material-UI integration

### 3. Data Visualization
- Multiple chart types (line, pie, choropleth)
- Interactive legends and tooltips
- Responsive chart sizing

### 4. State Management
- Redux Toolkit for global state
- RTK Query for API caching
- Optimistic updates

### 5. Advanced DataGrid Features
- Server-side pagination
- Column sorting
- Search functionality
- Custom cell rendering

## POC Success Metrics

✅ **Backend API**: All endpoints responding correctly
✅ **Database**: Sample data loaded and accessible
✅ **Frontend**: All routes navigable
✅ **Charts**: Data visualizations rendering
✅ **Responsive**: Works on mobile and desktop
✅ **Theme**: Dark/light mode switching
✅ **Performance**: Fast loading and smooth interactions

## Quick Troubleshooting

### Backend Issues
```bash
# Check if server is running
curl http://localhost:5001/general/user/63701cc1f03239b7f700000e

# Check MongoDB connection
# Ensure MongoDB is running on port 27017
```

### Frontend Issues
```bash
# Check environment variables
echo $REACT_APP_BASE_URL

# Clear cache and restart
rm -rf node_modules package-lock.json
npm install
npm start
```

### Database Issues
```bash
# Check MongoDB status
mongosh
show dbs
use admin-dashboard
show collections
```

## POC Presentation Points

1. **Full-Stack Architecture**: React + Express + MongoDB
2. **Modern UI**: Material-UI with custom theming
3. **Data Visualization**: Multiple chart types with Nivo
4. **State Management**: Redux Toolkit with RTK Query
5. **Responsive Design**: Mobile-first approach
6. **Performance**: Optimized API calls and caching
7. **Scalability**: Modular component architecture
8. **User Experience**: Smooth navigation and interactions

This POC demonstrates a production-ready admin dashboard foundation that can be extended for specific business needs.