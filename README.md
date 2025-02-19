# Hadoop & Spark-Based Image Compression
![image](https://github.com/user-attachments/assets/c9bc801f-28dd-4fb5-b038-a1d7871ea37b)


## 📌 Project Overview
This project implements an image compression pipeline using **Hadoop** and **Apache Spark** in a **multi-node cluster** environment. The goal is to explore how Big Data technologies can be leveraged for efficient, distributed image compression using **JPEG2000 (Spark)** and **JPEG (MapReduce)**.
- find the execution videos for both jobs on the playlist : https://youtube.com/playlist?list=PLBJKqLIo6Tc9O80NMt_BO0LDYmf-k-c_T&si=k80_PjS8aWqYvVbb

## 🎯 Objectives
- **Deploy a Multi-Node Hadoop Cluster**: Setup and configure Hadoop & Spark for distributed processing.
- **Implement Image Compression Algorithms**: Use **JPEG2000** (Spark) and **JPEG** (Hadoop MapReduce).
- **Compare Performance**: Analyze speed, scalability, and efficiency of **Hadoop vs. Spark** for image processing.

## 🛠 Technologies Used
- **Hadoop** (HDFS, MapReduce)
- **Apache Spark** (RDDs, PySpark)
- **Java & Python**
- **VMware Workstation** (Multi-Node Setup)
- **Ubuntu 20.04**
- **OpenCV & Pillow** (Image Processing)

## ⚙️ System Setup
### **1. Hadoop Multi-Node Cluster Setup**
- Install Java 8, Hadoop 3.3.6, and configure SSH.
- Setup HDFS, MapReduce, and YARN.
- Configure master and worker nodes.

### **2. Spark Configuration**
- Install and configure Apache Spark 3.4.4.
- Update `spark-env.sh` and distribute configs to worker nodes.

### **3. HDFS Storage & Image Upload**
- Store raw images in HDFS (`/user/hadoop/input_images`).
- Processed images are stored in `/user/hadoop/compressed_images`.

## 🔥 Implementation Approaches
### **1️⃣ Spark-Based JPEG2000 Compression**
- Uses PySpark for parallel processing.
- Reads images from HDFS, compresses using `JPEG2000`, and stores back in HDFS.

### **2️⃣ Hadoop MapReduce-Based JPEG Compression**
- Uses custom **Java MapReduce** implementation.
- Processes images in parallel using WholeFileInputFormat.

## 🚀 Running the Project
### **1. Start Hadoop & Spark Services**
```bash
start-dfs.sh
start-yarn.sh
$SPARK_HOME/sbin/start-master.sh
$SPARK_HOME/sbin/start-workers.sh
```

### **2. Upload Images to HDFS**
```bash
hdfs dfs -mkdir -p /user/hadoop/input_images
hdfs dfs -put ~/Desktop/Hadoop-job/images/* /user/hadoop/input_images
```

### **3. Submit Spark Job for JPEG2000 Compression**
```bash
spark-submit --master yarn --deploy-mode cluster Desktop/Hadoop-job/jpeg2000_compression.py
```

### **4. Run MapReduce Job for JPEG Compression**
```bash
hadoop jar imagecompressor.jar ImageCompressor /user/hadoop/input_images /user/hadoop/compressed_images
```

### **5. Retrieve Results from HDFS**
```bash
hdfs dfs -get /user/hadoop/compressed_images ~/Desktop/Hadoop-job/compressed
```

## 📊 Performance Comparison
| Approach   | Compression Type | Execution Speed | Scalability |
|------------|----------------|----------------|-------------|
| **Spark** | JPEG2000 | 🚀 Faster (In-Memory) | ✅ High |
| **MapReduce** | JPEG | 🐢 Slower (Disk-Based) | ✅ High |

## 📝 Conclusion
Both **Hadoop MapReduce** and **Spark** offer efficient distributed image compression, but **Spark** significantly improves processing speed due to in-memory execution. **Hadoop MapReduce**, while slower, remains a stable choice for batch processing in constrained environments.

## 👥 Contributors
- **Abdelatif Mekri**
- **Halima Nfidsa**
- [**Imad Eddine Boukader**](https://github.com/ispollin)
- **Nahla Yasmine Mihoubi**

