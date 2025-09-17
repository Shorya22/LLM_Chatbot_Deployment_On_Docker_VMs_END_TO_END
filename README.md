# 🤖 Gemini Chatbot Deployment  

![Python](https://img.shields.io/badge/Python-3.11-blue)  
![Streamlit](https://img.shields.io/badge/Streamlit-Chatbot-red)  
![Docker](https://img.shields.io/badge/Docker-Containerized-blue)  
![Gemini API](https://img.shields.io/badge/Google-Gemini--API-green)  
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-orange)  

A **Streamlit-based chatbot** powered by **Google Gemini API**, containerized with **Docker**, and deployed on an **Ubuntu VM (VirtualBox)**.  

This project demonstrates how to build, containerize, and deploy an on-premise AI chatbot using modern tools.  

---

## 🚀 Project Goal  
- Build a chatbot interface with **Streamlit**  
- Integrate with **Google Generative AI SDK (Gemini API)**  
- Containerize using **Docker**  
- Deploy on **Ubuntu 24 (VirtualBox VM)**  
- Enable portability with `.tar` Docker image export/import  

---

## 🛠️ Tech Stack  
- **Frontend**: Streamlit (Python)  
- **AI Model**: Google Gemini (`gemini-pro`)  
- **Containerization**: Docker  
- **Deployment**: Ubuntu 24 VM on VirtualBox  
- **Networking**: Bridged Adapter, SSH, SCP  

---

## 📂 Project Structure  
```
chatbot_project/
├── app.py              # Streamlit app
├── requirements.txt    # Dependencies
├── Dockerfile          # Containerization
└── gemini_chatbot.tar  # Generated Docker image (after build)
```

---

## ⚙️ Setup & Deployment  

### 1️⃣ Local Setup (Windows Host)  
```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

### 2️⃣ Build & Export Docker Image  
```bash
docker build -t gemini-chatbot .
docker save gemini-chatbot > gemini_chatbot.tar
```

### 3️⃣ Transfer to Ubuntu VM  
```bash
scp gemini_chatbot.tar admin@<VM_IP>:/home/admin/
```

### 4️⃣ Load & Run in Ubuntu VM  
```bash
docker load < gemini_chatbot.tar
docker run -e GEMINI_API_KEY="YOUR_API_KEY" -p 8501:8501 gemini-chatbot
```

### 5️⃣ Access Chatbot  
- Inside VM: [http://localhost:8501](http://localhost:8501)  
- From LAN: `http://<VM_IP>:8501`  

---

## 🔑 Notes  
- Ensure you have a valid **Gemini API Key** (`GEMINI_API_KEY`).  
- Open port `8501` if accessing from external devices.  
- Use `docker run -d` for background execution.  
- Optional: Configure **Docker Compose**, logging, and auto-restart for production.  

---

## ✅ Outcome  
Your chatbot is now:  
- 🐳 **Dockerized**  
- 📦 **Portable via image export/import**  
- 💻 **Deployed inside an Ubuntu VM**  

---

## 📸 Demo (Optional)  
_Add screenshots of the chatbot interface here for better presentation._  

---

## 📜 License  
This project is licensed under the **MIT License** – feel free to use and modify.  
