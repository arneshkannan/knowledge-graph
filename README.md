# A Self-Updating Organizational Knowledge System Using Generative AI

[![React](https://img.shields.io/badge/React-19.0-61dafb.svg?logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3178c6.svg?logo=typescript)](https://www.typescriptlang.org/)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth%20%7C%20Storage-ffca28.svg?logo=firebase)](https://firebase.google.com/)
[![Google Gemini API](https://img.shields.io/badge/Google_Gemini_API-3.8_Flash_(Free_Tier)-4285f4.svg?logo=google)](https://aistudio.google.com/)
[![Knowledge Graph](https://img.shields.io/badge/Graph-Cytoscape.js-10b981.svg)](https://js.cytoscape.org/)
[![Vite](https://img.shields.io/badge/Bundler-Vite_6-646cff.svg?logo=vite)](https://vitejs.dev/)

> **A student/final-year enterprise software engineering project** designed to run on **100% Free-Tier / Freely Available Services** (Firebase Spark Plan + Google Gemini API Free Tier). Zero paid database services (No PostgreSQL, No MongoDB, No Neo4j, No paid OpenAI API).

---

## 1. System Vision & Central Architecture

In complex multi-department organizations, managers often oversee dozens of simultaneous projects. Crucial project reality is fragmented across scattered weekly reports, task tickets, meeting transcripts, pull requests, and risk assessments. Rather than forcing managers to read every document or chase teams for manual updates, **Generative AI continuously transforms raw document updates into connected, structured organizational knowledge stored in Cloud Firestore, updates an interactive Knowledge Graph, and re-evaluates the true project lifecycle stage and condition.**

```
                                  ORGANIZATIONAL WORKFLOW
                                  
       ┌────────────────────────┐
       │   MANAGER / DIRECTOR   │
       └───────────┬────────────┘
                   │ 1. Selects Department & Project
                   ▼
       ┌────────────────────────┐
       │  DEPARTMENT & PROJECT  │ (e.g., Software Development -> Employee Management System)
       └───────────┬────────────┘
                   │ 2. Queries Knowledge Base
                   ▼
       ┌────────────────────────────────────────────────────────┐
       │      FIRESTORE ORGANIZATIONAL KNOWLEDGE BASE           │
       │  (projects, tasks, milestones, documents, auditLogs)   │
       └───────────┬────────────────────────────┬───────────────┘
                   │                            │
                   ▼                            ▼
       ┌────────────────────────┐   ┌───────────────────────────┐
       │   KNOWLEDGE GRAPH      │   │  GEMINI AI RAG ASSISTANT  │
       │ (Nodes & Relationships)│   │(Grounded Evidence Answers)│
       └───────────▲────────────┘   └─────────────▲─────────────┘
                   │                              │
                   │ 4. Graph Updates             │ 3. Continuous Analysis
                   │                              │
       ┌───────────┴──────────────────────────────┴─────────────┐
       │             AUTONOMOUS SELF-UPDATING PIPELINE          │
       │                                                        │
       │  New Document Upload / Progress Report Ingestion       │
       │                      ↓                                 │
       │  Gemini AI Entity & Deliverable Extraction             │
       │                      ↓                                 │
       │  System Delta Change Detection (Old vs New Values)     │
       │                      ↓                                 │
       │  Stage Analysis Engine (e.g. DEVELOPMENT → TESTING)    │
       │                      ↓                                 │
       │  Condition Scoring Engine (ON TRACK / AT RISK / BLOCKED)
       │                      ↓                                 │
       │  Immutable Audit Log Appended (projectStatusHistory)   │
       └────────────────────────────────────────────────────────┘
```

---

## 2. End-to-End Demonstration Scenario

The prototype is engineered to demonstrate the exact workflow:

1. **Step 1:** Manager logs into the platform (pre-authenticated as Engineering Director *Sarah Jenkins*).
2. **Step 2:** Manager views the **Executive Knowledge & Portfolio Dashboard** with organization-wide metrics (5 departments, monitored projects, active vs completed, at-risk alerts).
3. **Step 3:** Manager selects **Software Development** department.
4. **Step 4:** Manager sees the three projects belonging to Software Development:
   - *Employee Management System* (Development, 65%, On Track, Medium Risk)
   - *Inventory Management System* (Design, 35%, On Track, Low Risk)
   - *Customer Portal* (Testing, 88%, At Risk, High Risk)
5. **Step 5:** Manager selects **Employee Management System**.
6. **Step 6:** System displays:
   - **Current Stage:** `DEVELOPMENT` (Confidence: 92%)
   - **Overall Progress:** `65%`
   - **Condition:** `ON TRACK`
   - **Risk Level:** `MEDIUM`
7. **Step 7:** Manager clicks **Knowledge Graph**.
8. **Step 8:** The interactive graph displays all connected entities: Organization (`TechCorp Global`), Department (`Software Development`), Project, Manager, Team Leads, Tasks, Milestones, Documents, Technologies, and Risks.
9. **Step 9:** Manager clicks node **Frontend Development (75%)**:
   - Drawer opens displaying: Progress: `75%`, Status: `IN_PROGRESS`, Assigned: `Alex Chen`, Source Document: `EMS_Progress_Report_v2.txt`.
10. **Step 10:** Manager opens **Gemini AI Assistant** and asks:
    > *"Why is this project not in testing yet?"*
    
    Gemini answers strictly grounded in stored Firestore evidence:
    > *"The project is not yet ready for testing because frontend integration is 75% complete and API integration is 60% complete. Testing tasks remain pending and cannot proceed until core development dependencies reach 100% completion according to the latest project progress report."*
11. **Step 11:** Manager clicks **Self-Update Knowledge** and selects **"Demo Step 11: Progress Report v3 (Dev Complete -> Testing)"** (or uploads a custom report).
12. **Step 12:** The AI pipeline runs live:
    - **Document text is extracted.**
    - **Gemini extracts entities & deliverable metrics.**
    - **Change Detection detects:**
      * Frontend development: `75%` → `100%` (COMPLETED)
      * API integration: `60%` → `100%` (COMPLETED)
      * Unit testing: `0%` → `25%` (IN_PROGRESS)
      * Overall project progress: `65%` → `82%`
13. **Step 13:** The system automatically updates:
    - Firestore `tasks` and `projects` records
    - Knowledge graph nodes and edges (`Frontend Development` turns green `100%`, `Stage: TESTING`)
    - Project stage re-evaluated: **`DEVELOPMENT` → `TESTING`**!
    - Project condition re-evaluated: **`ON TRACK`**
    - Explainable AI summary regenerated
    - Audit history logs:
      *"Frontend Development progress changed from 75% to 100% based on EMS_Progress_Report_v3_DevComplete.txt"*
      *"Project stage transitioned from DEVELOPMENT to TESTING"*
14. **Step 14:** Manager returns to the dashboard to see the live updated project state!

---

## 3. Technology Stack & Free-Tier Compliance

| Component | Technology | Free Tier Specification |
|---|---|---|
| **Frontend** | React 19, TypeScript, Vite 6, Tailwind CSS v4 | Local client execution, zero hosting overhead |
| **Authentication** | Firebase Authentication | Free Spark Plan (Email/Password, 50k monthly active users free) |
| **Database** | Firebase Cloud Firestore | Free Spark Plan (50,000 reads/day, 20,000 writes/day, 1GB storage free) |
| **File Storage** | Firebase Storage | Free Spark Plan (5GB storage, 1GB download/day free) |
| **Generative AI** | Google Gemini API (`gemini-3.8-flash`) | Google AI Studio Free Tier (15 RPM, 1M TPM, 1,500 RPD free) |
| **Knowledge Graph** | Cytoscape.js & Cytoscape-Dagre | Client-side Canvas/WebGL graph theory engine (replaces expensive Neo4j) |
| **Backend/Proxy** | Node.js / Express (Optional proxy in `/server`) | Lightweight API proxy for secure `GEMINI_API_KEY` handling |

> [!NOTE]
> **No Paid Databases**: Uses Firebase Cloud Firestore instead of PostgreSQL, MongoDB, or Neo4j.
> **No Paid AI APIs**: Uses Google Gemini API free-tier via `@google/genai` instead of OpenAI.
> **High-Fidelity Demo Mode**: If no Firebase credentials or Gemini API key are provided, the application runs 100% out-of-the-box using local persistent Firestore simulation and rule-based heuristic AI!

---

## 4. Firestore Data Models

Data collections in Cloud Firestore:

- `departments/{departmentId}`: Department metadata, manager credentials, project counts, progress.
- `projects/{projectId}`: Core project records, stage, condition, risk, progress %, owners.
- `tasks/{taskId}`: Task deliverable, assigned team member, status, progress (0-100), due date, source document.
- `milestones/{milestoneId}`: Milestone deliverables, target dates, completion status.
- `documents/{documentId}`: Document metadata, file size, storagePath, extractedText, processingStatus.
- `knowledgeNodes/{nodeId}`: Graph nodes (`Organization`, `Department`, `Project`, `Task`, `Milestone`, `Document`, `Employee`, `Risk`, `Technology`, `ProjectStage`, `ProjectStatus`).
- `knowledgeRelationships/{relId}`: Graph edges (`HAS_DEPARTMENT`, `OWNS_PROJECT`, `HAS_TASK`, `HAS_STAGE`, `ASSIGNED_TO`, `DEPENDS_ON`, `DESCRIBES`, etc.).
- `projectStatusHistory/{historyId}`: Chronological change log entries.
- `auditLogs/{auditId}`: Immutable system audit trail.

---

## 5. Quick Start & Setup Guide

### Prerequisites
- Node.js >= 18.0.0 (Node 24 LTS verified)
- Free Google Gemini API Key (from [Google AI Studio](https://aistudio.google.com/))
- Free Firebase Project (from [Firebase Console](https://console.firebase.google.com/))

### Installation
```bash
# Clone or navigate to the project directory
cd "S5 mini project"

# Install dependencies
npm install
```

### Running the Application

#### Option A: Instant Run in Demo Mode (Zero Setup Needed)
```bash
npm run dev
```
Open `http://localhost:5173` in your browser. The application will immediately boot in **High-Fidelity Demo Mode** with complete seed data for 5 departments and 12 projects!

#### Option B: Connecting Live Gemini API Key
1. Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   ```
2. Insert your free Gemini API key:
   ```env
   GEMINI_API_KEY=AIzaSy...
   VITE_GEMINI_API_KEY=AIzaSy...
   ```
3. Alternatively, click the **Settings** gear icon in the top right of the running application and paste your Gemini API key directly into the session modal!

#### Option C: Connecting Live Firebase Cloud Firestore
1. In [Firebase Console](https://console.firebase.google.com/), create a free project.
2. Enable **Authentication** (Email/Password), **Cloud Firestore**, and **Firebase Storage**.
3. Deploy security rules:
   - Paste contents of `firestore.rules` into Firebase Firestore Rules.
   - Paste contents of `storage.rules` into Firebase Storage Rules.
4. Populate your `.env`:
   ```env
   VITE_FIREBASE_API_KEY=AIzaSy...
   VITE_FIREBASE_AUTH_DOMAIN=your-app.firebaseapp.com
   VITE_FIREBASE_PROJECT_ID=your-app
   VITE_FIREBASE_STORAGE_BUCKET=your-app.appspot.com
   VITE_FIREBASE_MESSAGING_SENDER_ID=...
   VITE_FIREBASE_APP_ID=...
   ```
5. Click **Settings** in the app and click **"Push Sample Collections to Firestore"** to seed all 5 departments, projects, tasks, and knowledge nodes into your live Cloud Firestore database with a single click!

#### Option D: Running with the Secure Backend API Proxy
```bash
# Terminal 1: Backend Express Server
npm run server

# Terminal 2: React Frontend
npm run dev
```

---

## 6. Android APK Build & Deployment Guide

The application is fully configured as a native Android app using **Capacitor**:
- **Package ID:** `io.techcorp.knowledgesystem`
- **Application Name:** `Org Knowledge System`
- **Native Project Folder:** `android/`
- **Network Permissions:** `android.permission.INTERNET` configured in `AndroidManifest.xml`

### How to Build the `.apk` File:

#### Step 1: Sync Web Assets to Android Project
Whenever you update code or build a new release, sync the assets:
```bash
npm run build:android
```
This runs `vite build` and updates `android/app/src/main/assets/public/` with the latest bundles.

#### Step 2: Generate the APK

##### Method A: One-Click Build via Android Studio (Recommended)
1. Open the Android project in Android Studio:
   ```bash
   npm run cap:open
   ```
2. Android Studio will open the `./android` directory and sync Gradle automatically.
3. In the top menu bar, click:
   **Build > Build Bundle(s) / APK(s) > Build APK(s)**
4. When the build finishes, click the **"locate"** popup link.
5. Your ready-to-install Android APK will be at:
   `android/app/build/outputs/apk/debug/app-debug.apk`

##### Method B: Command-Line Build via Gradle
```bash
cd android
./gradlew assembleDebug
```
(On Windows: `.\gradlew.bat assembleDebug`)

The generated debug APK will be created at:
`android/app/build/outputs/apk/debug/app-debug.apk`

You can transfer `app-debug.apk` to any Android phone or tablet via USB, Google Drive, or email and install it directly!

---

## 6. Project Stage & Condition Analysis Engine

### Stage Lifecycle Order
1. `INITIATION`
2. `REQUIREMENTS`
3. `PLANNING`
4. `DESIGN`
5. `DEVELOPMENT` (Execution)
6. `TESTING`
7. `DEPLOYMENT` (Implementation)
8. `COMPLETED`

### Stage Exit Criteria
- **Transition from DESIGN → DEVELOPMENT**: Requirements and database schema design reach 100%.
- **Transition from DEVELOPMENT → TESTING**: Frontend development and API integration reach 100%, and unit testing tasks commence.
- **Transition from TESTING → DEPLOYMENT**: Unit testing and user acceptance testing (UAT) reach 100% with stakeholder sign-off.
- **Transition from DEPLOYMENT → COMPLETED**: Production rollout verified.

### Condition Scoring Factors
- `ON TRACK`: Task progress velocity aligns with milestone deadlines and zero blocker risks.
- `AT RISK`: Unresolved high-severity risk (e.g. SSO gateway throttle or third-party API latency).
- `DELAYED`: Target milestone delivery dates have slipped beyond scheduled buffer.
- `BLOCKED`: Core deliverable has dependency tasks in blocked status.
- `COMPLETED`: All project deliverables 100% achieved.

---

## 7. Interactive Knowledge Graph Features

- **Cytoscape.js Canvas**: Smooth WebGL/Canvas rendering with zero lag.
- **Layout Switcher**:
  - `Hierarchical (Dagre)`: Top-down organizational DAG.
  - `Force-Directed (Cose)`: Physics-based repulsive clustering.
  - `Concentric`: Radial concentric orbits centered on the project.
  - `Circle`: Perimeter layout.
- **Interactive Controls**: Zoom In, Zoom Out, Fit View, Reset.
- **Type Filter Pills**: Toggle visibility of Tasks, Milestones, Documents, Team, Risks, Tech, Stage, or Status nodes.
- **Node Search**: Real-time spotlighting and neighborhood highlighting.
- **Slide-Over Node Inspector**:
  - Click any **Task**: Inspect progress bar, assignee, status, dependencies, and citation document.
  - Click any **Document**: Inspect filename, version, upload date, and extracted text preview.
  - Click any **Stage**: View evaluated stage and supporting evidence grounding.
  - Click any **Risk**: View severity level and mitigation strategy.

---

## 8. Verification & Test Checklist

- [x] Node.js 24 LTS and npm verified
- [x] React 19 + TypeScript + Vite 6 compiles cleanly with 0 errors (`npm run build`)
- [x] Cytoscape.js and Dagre graph library rendering verified
- [x] Firebase Client & Firestore CRUD service verified
- [x] Google Gemini API integration (`gemini-3.8-flash`) implemented
- [x] Demo Mode / Grounded Heuristic fallback implemented for zero-friction evaluation
- [x] End-to-end self-updating pipeline (Ingest -> Extract -> Change Detect -> Update DB -> Update Graph -> Recalculate Stage) verified
- [x] RAG grounded AI assistant with evidence citation verified
- [x] Firestore security rules (`firestore.rules`) and Storage security rules (`storage.rules`) provided
- [x] Environment configuration template (`.env.example`) provided

---

## 9. License & Academic Attribution
Developed as an academic / final-year software engineering prototype for organizational project intelligence and self-updating knowledge systems using Generative AI.
