Here’s an **enhanced `README.md`** with a strong *development journey / iteration section* added — this is exactly what makes your project stand out professionally 👇

---

# 🏡 Airbnb Booking Assistant (Bangkok Listings)

## 📌 Overview

This project builds a **GPT-powered AI booking assistant** that helps users search and explore Airbnb-style listings in Bangkok using a structured dataset.

The assistant is designed as a **tool-using AI agent**, capable of:

* Understanding user intent (location, room type, preferences)
* Searching listings from an internal dataset
* Recommending top-performing properties based on occupancy rate
* Guiding users toward booking decisions

---

## 🎯 Project Goal

The main objective is to simulate a **high-conversion booking assistant** that:

* Promotes the most popular listings (high occupancy rate)
* Provides relevant recommendations based on user input
* Encourages users to proceed toward booking

---

## ⚙️ Features

### 🔍 Smart Search (Top 10 Listings)

* Search by **neighbourhood** (with fuzzy matching)
* Automatically ranks listings by **occupancy rate**
* Returns top 10 most in-demand properties

---

### 🧠 GPT-powered AI Agent

* Uses OpenAI function-calling (tool usage)
* Decides dynamically when to:

  * Search listings
  * Recommend options
  * Proceed to booking flow

---

### 🏠 Room Type Understanding

* Maps flexible user input into structured values:

  * “entire apartment” → `entire home/apt`
  * “private room” → `private room`

---

### 📅 Date Normalization

* Converts natural language into standard format (`YYYY-MM-DD`)

---

### 📦 Tool-Based Architecture

| Tool              | Purpose                                |
| ----------------- | -------------------------------------- |
| `search_listings` | Retrieve top listings by neighbourhood |
| `book_listing`    | Simulate booking                       |

---

## ⚠️ Important Limitation

> 🚨 **Booking is currently simulated only**

The dataset **does NOT include availability data**, such as:

* Check-in / check-out availability
* Booking calendar per listing

### ❌ Current limitations:

* Cannot validate real availability
* Cannot prevent double booking
* Cannot perform real transactions

### ✅ Current behavior:

* Accepts booking intent
* Returns a **simulated confirmation message**

---

## 🧱 Project Structure

```bash
airbnb-agent/
│
├── notebook.ipynb
├── listings.csv
├── requirements.txt
└── README.md
```

---

## 🚀 How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

---

### 2. Set API Key

Create `.env` file:

```bash
OPENAI_API_KEY=your_api_key_here
```

---

### 3. Run the Notebook

```python
run_agent()
```

---

## 💬 Example Interaction

```text
User: Find me a place in Sukhumvit

Assistant:
→ Calls search_listings
→ Returns top listings

User: I want the first one, entire apartment

Assistant:
→ Simulates booking
→ "Booked XYZ Apartment from 2025-05-01 to 2025-05-03"
```

---

# 🔧 Development Journey & Iteration

This project was built iteratively by refining both **data logic** and **AI agent behavior**.

## 🧪 1. Initial Version (Baseline)

* Simple dataset loading
* Basic search using exact match
* No ranking or intelligence
* No AI agent (manual function calls)

---

## 🔍 2. Improved Search Quality

* Introduced **fuzzy matching (RapidFuzz)**
  → Handles user inputs like:

  * “Sukumvit” → “Sukhumvit”
* Switched from exact filtering → **user-friendly search**

---

## 📊 3. Ranking Optimization

* Engineered **occupancy_rate**:

```python
occupancy_rate = (365 - availability_365) / 365
```

* Used as a proxy for:

  * Demand
  * Popularity
  * Conversion likelihood

→ Enabled **top 10 recommendation strategy**

---

## 🧠 4. Introduced AI Agent (LLM Integration)

* Integrated GPT with:

  * Tool calling
  * Conversation memory
* Agent can:

  * Decide when to search
  * Interpret user intent
  * Drive booking flow

---

## 🔁 5. Agent Loop Fixes (Critical Learning)

### ❌ Early issues:

* Agent stopped after tool call
* No final response returned
* Infinite loops / incomplete reasoning

### ✅ Fix:

* Implemented **inner loop**
* Ensured:

  * Tool results are appended to messages
  * Agent continues reasoning after tool call
  * Proper termination when final answer is generated

---

## 🧩 6. Tool Design Improvements

* Structured tools with:

  * Clear input schema
  * JSON-based output
* Added:

  * `search_listings`
  * `book_listing`

→ Enables **deterministic + explainable behavior**

---

## 🏠 7. User Intent Normalization

* Added:

  * Room type mapping
  * Date parsing
* Reduced ambiguity in user input

---

## 🎯 8. Conversion-Oriented Prompt Design

Refined system prompt to enforce:

* ❌ No hallucination
* ❌ No external platform suggestion
* ✅ Always use tool data
* ✅ Always guide toward booking

→ Shift from **chatbot → sales agent mindset**

---

## 🧹 9. Code Refactoring & Cleanup

* Removed:

  * Colab-specific dependencies
  * Hardcoded API keys
  * Redundant imports
* Improved:

  * Modularity
  * Readability
  * Reusability

---

## 🧠 Key Learnings

* AI agents require **loop control**, not just API calls
* Tool design is as important as model capability
* Data quality directly impacts recommendation quality
* Prompt design strongly affects **conversion behavior**

---

## 🔮 Future Improvements

### 📅 Add Real Availability

* Introduce booking calendar
* Enable real validation before booking

---

### 🌐 Build UI

* Streamlit / Web app
* Real booking interface

---

### 📊 Add Analytics

* Track:

  * User search behavior
  * Conversion funnel
  * Popular listings

---

### 🧠 Personalization

* Remember user preferences
* Recommend based on history

---

## 👤 Author

This project demonstrates:

* AI Agent architecture (LLM + tools + loop)
* Data-driven recommendation system
* Real-world booking assistant simulation
* Iterative system design and refinement

