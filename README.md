<div align="center">

# 🎓 SmartTutor

### AI-Powered Learning Assistant — Turn Any Document Into Flashcards, Quizzes & a Personal Tutor

Upload your notes or PDFs and let AI generate summaries, flashcards, and quizzes — then chat with an AI tutor about the content and track your learning progress over time.

[![Live App](https://img.shields.io/badge/Live%20App-smart--learning--assistant-2ea44f?style=for-the-badge&logo=vercel)](https://smart-learning-assistant-l8ny.vercel.app/)
[![Node.js](https://img.shields.io/badge/Node.js-Express%205-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://expressjs.com/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Gemini AI](https://img.shields.io/badge/Google%20Gemini-AI-4285F4?style=for-the-badge&logo=google-gemini&logoColor=white)](https://ai.google.dev/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge&logo=mongodb)](https://www.mongodb.com/)

[🚀 Live App](https://smart-learning-assistant-l8ny.vercel.app/) · [🐛 Report Bug](https://github.com/manish1404-rgd/SmartTutor/issues) · [✨ Request Feature](https://github.com/manish1404-rgd/SmartTutor/issues)

</div>

---

## 📖 About The Project

**SmartTutor** is a full-stack AI learning companion. Upload a PDF, image, or document, and it automatically extracts the text (using OCR for scanned pages), then uses **Google Gemini AI** to generate concise summaries, concept explanations, flashcard decks, and quizzes straight from your material. An integrated AI chat lets you ask follow-up questions about your document, while a progress dashboard tracks how you're improving over time.

Think of it as a **personal AI tutor** that studies your notes with you.

---

## ✨ Features

- 📄 **Smart Document Upload** — Upload PDFs or images; text is extracted via `pdf-parse` and **Tesseract.js OCR** (with Google Cloud Vision support) for scanned content.
- 🤖 **AI-Generated Study Material** — Automatically generate:
  - 📝 **Summaries** of uploaded content
  - 🧠 **Flashcard decks** for active recall
  - ❓ **Quizzes** to test your understanding
  - 💡 **Concept explanations** on demand
- 💬 **AI Tutor Chat** — Chat with an AI about your uploaded documents, with full chat history saved per document.
- 🔁 **Flashcard Review System** — Review flashcards, star/favorite important ones, and revisit sets anytime.
- 🧪 **Quiz Engine** — Take auto-generated quizzes, submit answers, and view detailed results.
- 📊 **Progress Dashboard** — Track your study activity, quiz performance, and flashcard mastery over time.
- 🔐 **Secure Authentication** — JWT-based auth with registration, login, profile management, and password change.
- ☁️ **Cloud File Storage** — Uploaded documents/media are stored via **Cloudinary**.
- 🎨 **Smooth, Modern UI** — Built with React 19, Tailwind CSS, and Framer Motion animations.

---

## 🛠️ Tech Stack

### Backend

| Category | Technology |
|---|---|
| **Runtime/Framework** | Node.js, Express 5 |
| **Database** | MongoDB with Mongoose |
| **Authentication** | JWT, bcrypt/bcryptjs |
| **AI** | Google Gemini API (`@google/genai`) |
| **OCR / Parsing** | Tesseract.js, Google Cloud Vision, `pdf-parse`, `pdf2pic` |
| **File Uploads** | Multer, Cloudinary |
| **Validation** | express-validator |

### Frontend

| Category | Technology |
|---|---|
| **Framework** | React 19 + Vite |
| **Styling** | Tailwind CSS |
| **Animation** | Framer Motion |
| **Routing** | React Router DOM v7 |
| **HTTP Client** | Axios |
| **Markdown Rendering** | react-markdown + remark-gfm + react-syntax-highlighter |
| **Notifications** | react-hot-toast |
| **Auth Utils** | jwt-decode |

---

## 📂 Project Structure

```
SmartTutor/
├── backend/
│   ├── src/
│   │   ├── controllers/       # auth, document, ai, flashcard, quiz, progress logic
│   │   ├── routes/            # /auth /documents /ai /flashcards /quizess /progress
│   │   ├── models/            # User, Document, Flashcard, Quiz, AIChatHistory schemas
│   │   ├── middlewares/       # JWT auth guard, global error handler
│   │   ├── utils/             # PDF parser, text chunker, Gemini service, Cloudinary uploader
│   │   ├── config/            # Multer file-upload config
│   │   ├── db/                # MongoDB connection
│   │   └── server.js          # Express app entry point
│   └── package.json
│
└── frontend/
    └── vite-project/
        ├── src/
        │   ├── components/     # auth, chat, documents, flashcards, quizzes, layout, common
        │   ├── pages/           # dashboard, documents, flashcards, quizzes, auth, profile
        │   ├── context/          # Global React context (auth/session)
        │   ├── services/          # API service layer (Axios)
        │   └── utils/
        └── package.json
```

---

## 🔗 API Overview

| Module | Base Route | Description |
|---|---|---|
| **Auth** | `/api/v1/auth` | Register, login, get/update profile, change password |
| **Documents** | `/api/v1/documents` | Upload, list, fetch, update, delete documents |
| **AI** | `/api/v1/ai` | Generate flashcards, generate quiz, explain concept, chat, chat history, generate summary |
| **Flashcards** | `/api/v1/flashcards` | List, fetch, review, star/unstar, delete flashcard sets |
| **Quizzes** | `/api/v1/quizess` | List, fetch, submit, get results, delete quizzes |
| **Progress** | `/api/v1/progress` | Dashboard analytics |

All routes except registration/login are protected via JWT (`Authorization` header).

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+)
- A [MongoDB](https://www.mongodb.com/) database (local or Atlas)
- A [Google Gemini API key](https://ai.google.dev/)
- A [Cloudinary](https://cloudinary.com/) account
- *(Optional)* Google Cloud Vision credentials for enhanced OCR

### 1. Clone the repository

```bash
git clone https://github.com/manish1404-rgd/SmartTutor.git
cd SmartTutor
```

### 2. Backend setup

```bash
cd backend
npm install
```

Create a `.env` file inside `backend/`:

```env
PORT=8000
NODE_ENV=development
MONGODB_URL=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRES=7d
GEMINI_API_KEY=your_gemini_api_key
CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEYS=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

Run the backend:

```bash
npm run dev
```

### 3. Frontend setup

```bash
cd ../frontend/vite-project
npm install
npm run dev
```

Open the local URL shown in your terminal (usually [http://localhost:5173](http://localhost:5173)) 🎉

---

## 🧭 Usage

1. **Sign up / log in** to your account.
2. **Upload a document** (PDF or image) — text is extracted automatically.
3. Generate **summaries**, **flashcards**, or a **quiz** from the document with one click.
4. **Chat with the AI tutor** to clarify concepts or ask follow-up questions.
5. **Review flashcards** and **take quizzes** to reinforce learning.
6. Check your **progress dashboard** to see how you're improving over time.

---

## 🗺️ Roadmap

- [ ] Spaced-repetition scheduling for flashcards
- [ ] Multi-document collections / folders
- [ ] Export flashcards & quizzes as PDF
- [ ] Collaborative study groups
- [ ] Support for more file types (PPTX, DOCX)

Have an idea? Feel free to [open an issue](https://github.com/manish1404-rgd/SmartTutor/issues)!

---

## 🤝 Contributing

Contributions make the open-source community amazing. Any contributions you make are **greatly appreciated**.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 📬 Contact

**Manish Kumar Kuldeep**

[![GitHub](https://img.shields.io/badge/GitHub-manish1404--rgd-181717?style=for-the-badge&logo=github)](https://github.com/manish1404-rgd)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Manish%20Kumar%20Kuldeep-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/manish-kumar-kuldeep-a0631a293/)

Project Link: [https://smart-learning-assistant-l8ny.vercel.app/](https://smart-learning-assistant-l8ny.vercel.app/)

---

<div align="center">

If you found this project useful, consider giving it a ⭐ on GitHub!

</div>
