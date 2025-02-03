```markdown
# DataSet Explorer

## Deployment Links:
- **Live App:** [Insert Frontend Deployment Link Here]
- **Backend API:** [http://dataset-hugging.eba-aqwtjpfu.us-west-2.elasticbeanstalk.com/](http://dataset-hugging.eba-aqwtjpfu.us-west-2.elasticbeanstalk.com/)

---

## Tech Stack
### **Frontend**
- **Framework**: Next.js + TypeScript  
- **Authentication**: Clerk  
- **State Management**: Redux  
- **UI Components**: Tailwind CSS  
- **Integration Testing**: Playwright  
- **Logging**: Pino.js  

### **Backend**
- **Framework**: FastAPI  
- **Testing**: Pytest (Unit Testing)  
- **Model Training**: Google Colab (For Impact Analysis Model)  
- **Database**: MongoDB (No ORM Used)  

---

## **Images of All Features**
(Attach feature images here)

---

## **How to Run This Project Locally**
### **Frontend**
```sh
cd client
npm install
npm run dev
```

### **Backend**
```sh
cd server
python -m venv venv
source venv/bin/activate  # For macOS/Linux
venv\Scripts\activate  # For Windows
pip install -r requirements.txt
uvicorn app.main:app --reload
```

---

## **Feature Breakdown**
### **Follow**
- A simple MongoDB call to access the store.  
- Currently using MongoDB, but I prefer PostgreSQL for better scaling.

### **Impact Assessments**
- **Process**:
  1. Extract metadata from Hugging Face.  
  2. Extract size categories.  
  3. Normalize the data.  
  4. Apply **K-Means clustering** to classify datasets as **Low, Medium, High** impact.  
- **Training Code**: [Google Colab Notebook](https://colab.research.google.com/drive/1ocnd25RkpJchGXoGeWlc04zIALLfg1OX?usp=sharing)  
- Trained on **10,000 datasets**.

### **Combine Dataset**
- Supports `.json`, `.csv`, `.parquet` files.
- Extracts columns for selection.
- Provides **three** methods for merging datasets:
  1. **Union**
  2. **Intersection**
  3. **Concatenation**

---

## **Deployment Strategy**
- **Frontend**: Vercel  
- **Backend**: AWS Elastic Beanstalk  
- **Database**: MongoDB  

### **What Deployment Strategy Should Be Used (AWS)?**
- **Frontend**: Host on AWS Amplify / S3 + CloudFront  
- **Backend**: Use AWS Fargate or EC2 with Auto-Scaling  
- **Database**: Switch to **Amazon RDS (PostgreSQL)** or use **MongoDB Atlas**  

---

## **Scaling Strategies**
### **Handling API Scaling (Thousands to Millions of Requests Per Second)**
1. **Use an In-Memory Store (Redis)** to cache responses & reduce DB load.  
2. **Decouple impact analysis** via a **Kafka queue (or AWS SQS)**.  
3. **Implement a CDN (AWS CloudFront)** for caching.  
4. **Load Balancer (AWS ALB)** to distribute traffic efficiently.  

### **Scaling the Database**
- **Separate Read-Write Replicas** for better query performance.  
- **Use an Analytical DB (ClickHouse)** triggered by MongoDB.  
- **Prefer PostgreSQL on EC2 or RDS** for better scaling.  
- **Store impact assessment model files on AWS S3**.  

### **Monitoring & Debugging**
- **Implement Logging** (Pino.js for frontend, structured logging for backend).  
- **Monitor EC2 Performance** via AWS CloudWatch.  
- **Set Auto-Scaling Triggers** based on system load.  
- **Health Monitoring** with API response checks.  

### **Optimizing Database Queries**
- **Indexing** for faster lookups.  
- **Query Optimization** to improve execution plans.  
- **Use In-Memory Caching** for repeated queries.  

---

## **Development Tools Used**
- **Scrum Board**: [Trello](https://trello.com/invite/b/679679b5a4f65a46525a143f/ATTI73b2e5f504dc7df4b3b51258d78aceb06912738B/hugging-face-explorer)  

---

## **Current Application Issues**
❌ **Not utilizing Clerk for state management**  
❌ **Combine logic only processes 10 rows per dataset file**  

---


<h1 align="center">Hi 👋, I'm Ruturaj Chintawar</h1>
<h3 align="center">Currently pursuing a Master's in Computer Science @ USC</h3>

---
