# 📚 StudyBuddy AI — Custom Educational Content Generator

**StudyBuddy AI** is a web-based educational application that uses **Generative AI** to create personalised learning materials based on a user's topic, difficulty level, and preferred content type.

Whether you're studying **Photosynthesis, Python, Mathematics, History, or another subject**, StudyBuddy helps transform a topic into structured learning material that is easier to understand and use.

The application can generate **summaries, detailed notes, study guides, quizzes, and flashcards**, giving learners multiple ways to study and reinforce their knowledge.

---

## 🎯 Project Purpose

The goal of StudyBuddy AI is to improve access to quality educational content by allowing learners to generate **structured, personalised study materials on demand**.

Instead of searching through multiple resources to find suitable learning material, users can enter a topic and let StudyBuddy generate content tailored to their selected learning level.

---

## 💡 The Problem

Students often spend a significant amount of time searching for learning resources that match their:

* 📖 Specific topic
* 🎓 Knowledge level
* 🧠 Preferred learning format
* ⏰ Available study time

Generic educational resources may also be too difficult, too simple, or presented in a format that does not suit the learner.

### 💡 The Solution

StudyBuddy AI provides a single platform where learners can enter a topic, select their **difficulty level** and **content type**, and generate customised educational material using Generative AI.

---

## ✨ Key Features

### 📝 AI-Generated Summaries

Creates a short and clear overview of a topic, including important points and its real-world relevance.

### 📚 Detailed Notes

Generates structured notes divided into sections, with explanations and examples.

### 📖 Study Guides

Creates study guides containing key terms, definitions, examples, common mistakes, and summaries.

### 🧠 AI-Generated Quizzes

Generates multiple-choice questions with answer options, correct answers, and explanations to help learners test their knowledge.

### 🃏 Flashcards

Creates quick question-and-answer flashcards designed to support memorisation and revision.

### 🎓 Difficulty Levels

Users can select:

* 🟢 **Beginner**
* 🟡 **Intermediate**
* 🔴 **Advanced**

The AI adjusts the generated content according to the selected level.

### 📊 Study Progress Tracking

Generated content is saved to the user's study history, allowing them to return to previous topics and mark content as completed.

### 📄 PDF Downloads

Users can download generated educational content as PDF documents for offline study.

### ⏱️ Generation Information

The application displays information about how long content generation took and an estimate of the number of words processed.

---

## 🧩 How StudyBuddy Works

The application follows a simple five-step process:

### 1️⃣ Enter Your Topic

The user enters the subject or topic they want to learn.

Examples:

* `Photosynthesis`
* `Python`
* `Artificial Intelligence`
* `World War II`

The system validates the input before continuing.

### 2️⃣ Choose Your Difficulty Level

The learner selects **Beginner, Intermediate, or Advanced**.

This allows the AI to adjust the complexity and language of the generated material.

### 3️⃣ Select Content Type

The user chooses one of five learning formats:

| Content Type   | Purpose                            |
| -------------- | ---------------------------------- |
| 📝 Summary     | Quick overview of a topic          |
| 📚 Notes       | Detailed explanations and examples |
| 📖 Study Guide | Key concepts, terms, and mistakes  |
| 🧠 Quiz        | Test knowledge with MCQs           |
| 🃏 Flashcards  | Quick revision and memorisation    |

### 4️⃣ Generate Content

StudyBuddy creates an AI instruction based on the user's selections and sends it to **OpenAI GPT-4o-mini** through the Base44 `InvokeLLM` integration.

The AI returns the educational content in a structured format.

### 5️⃣ Save & Study

The generated material is displayed in a structured interface.

Users can:

* 👀 Read the content
* 📋 Copy it
* 📄 Download it as a PDF
* ✅ Mark it as read
* 💾 Return to it through study history
* 🗑️ Delete completed or unwanted content

---

## 🤖 AI & Prompt Engineering

StudyBuddy uses a structured prompt engineering approach based on the **CLEAR framework**.

### CLEAR Framework

**C — Contextual Role Assignment**
The AI is given an educator role to guide the style and quality of its response.

**L — Level-Aware Language Calibration**
The selected difficulty level determines how complex the explanation should be.

**E — Explicit Output Specification**
Each prompt clearly defines the required structure, format, and content limits.

**A — Actionable Content Bias**
The prompts produce useful learning materials such as quizzes, flashcards, examples, and further resources.

**R — Relevance Constraint**
The AI is instructed to remain focused on the requested topic and avoid unrelated information.

---

## 🧠 Prompt Templates

StudyBuddy uses five specialised prompt templates:

### 📝 Summary

Produces a concise overview, real-world importance, and key points.

### 📚 Notes

Produces structured learning notes with explanations, examples, and further resources.

### 📖 Study Guide

Provides key terms, definitions, examples, common mistakes, and a summary.

### 🧠 Quiz

Generates five multiple-choice questions with four answer options, correct answers, and explanations.

### 🃏 Flashcards

Generates five question-and-answer cards for quick memorisation and revision.

---

## 🏗️ Implementation Architecture

```text
User Input
    ↓
Input Validation
    ↓
Topic + Difficulty + Content Type
    ↓
Prompt Template Selection
    ↓
AI Instruction Generation
    ↓
OpenAI GPT-4o-mini
    ↓
Structured JSON Response
    ↓
JSON Schema Validation
    ↓
Content Display
    ↓
Save to Study History
    ↓
Progress Tracking
```

This architecture helps keep generated content consistent, structured, and easier for the application to process.

---

## 🛠️ Technologies Used

### Frontend

* ⚛️ **React 18** — User interface
* 🎨 **Tailwind CSS** — Styling and responsive design
* ✨ **Framer Motion** — Animations
* 🧭 **React Router** — Page navigation

### AI

* 🤖 **OpenAI GPT-4o-mini**
* 🔌 **Base44 InvokeLLM** — AI integration
* 🧠 **Prompt Engineering** — Structured educational prompts
* 📋 **JSON Schema** — Structured output validation

### Data & Documents

* 🗄️ **Base44 Entity Store** — Data storage
* 📄 **jsPDF** — PDF generation
* 💾 **Local caching** — Faster access to study history

---

## ⚡ Performance Optimisation

Several techniques were implemented to keep StudyBuddy responsive:

* ⚡ **Structured AI output** reduces additional processing.
* ✂️ **Short prompts** reduce unnecessary instructions.
* 🔄 **Loading animations** keep users informed while content is generated.
* 💾 **Background saving** prevents saving operations from blocking the interface.
* 🚀 **Local caching** reduces repeated history loading.
* 1️⃣ **Single AI call** generates each piece of content in one request.

---

## 🛡️ Input Validation & Error Handling

StudyBuddy includes several safeguards to improve reliability.

### Input Validation

The application prevents:

* Empty inputs
* Extremely short inputs
* Gibberish
* Numeric-only inputs
* Symbol-heavy inputs

Topics are also limited to **100 characters**, with a live character counter.

### Output Validation

AI responses are checked against a **JSON Schema** before being displayed to ensure the expected structure is returned.

### Request Control

The Generate button is disabled while content is being processed to help prevent duplicate requests.

### Error Handling

If an AI formatting or generation issue occurs, the application displays a clear retry message rather than silently failing.

---

## 🎯 Target Users

StudyBuddy AI is designed for:

* 👩‍🎓 Students
* 🧑‍🏫 Learners and educators
* 💻 People studying technology and programming
* 📚 Self-directed learners
* 🌱 Beginners learning new subjects
* 📝 Anyone who needs customised study material

---

## 🚀 Try StudyBuddy AI

Want to create your own personalised study material?

👉 https://brave-smart-study-sync.base44.app/

Enter a topic, choose your difficulty level, select how you want to study, and let **StudyBuddy AI** create your learning material. 📚🤖
