# The Media Tranquilizer #
**Value Truth, Not Noise**
The Media Tranquilizer (TMT) is an AI-powered, cross-runtime web extension engineered to mitigate the cognitive hazards of digital disinformation. By combining lightweight frontend injection with a localized, multi-threaded AI pipeline, TMT strips away media bias, sensationalism, and logical fallacies from video content in real-time—delivering objective truth directly to the user.

## Inspiration ##
Human error and societal polarization are heavily exacerbated by environmental and informational "noise." Whether it is the physical hazard of dense highway fog or the psychological toll of digital echo chambers, the underlying systemic flaw is the same: people cannot make sound decisions when they cannot see clearly. TMT was built to function as an algorithmic filter for the internet—algorithmic clarity replacing systemic uncertainty.

## System Architecture & Technical Execution
- **Frontend Integration:** Engineered a Google Chrome Developer Extension using native JavaScript and custom DOM manipulation, injecting an interactive UI overlay directly onto active YouTube video elements.
- **Asynchronous Audio Pipeline:** Automated automated media ingestion via `yt-dlp` paired with an optimized `faster-whisper` CoreML/CUDA pipeline to instantly extract local high-fidelity audio transcripts from video streaming packets.
- **Algorithmic Neutralization & NLP:** Leveraging the Google Gemini API with structured system prompting to run multi-layered linguistic analysis—parsing political bias, executing real-time cross-reference fact-checking, and generating objective truth matrices.
- **Bi-Directional Interactive Layer:** Developed a secondary user-engagement funnel using a containerized `Streamlit` architecture, transitioning users from static analysis to a dynamic 1-on-1 argumentative chat environment with the model.

The core technical challenge of this project was processing heavy multimedia data (video/audio) and running large language model inferences without introduces crippling latency or relying on expensive, privacy-invasive cloud video pipelines.
To solve this, I designed a decoupled, hybrid-runtime architecture (look at architecture.png for more info)

1. The Frontend (Chrome Extension)
Contextual Injection: A lightweight JavaScript content script injects a non-intrusive UI overlay directly into the YouTube DOM, dynamically tracking video states.
Asynchronous Communication: Dispatches non-blocking API requests to the local loopback address (localhost:3000), ensuring the browser UI never freezes during heavy computing cycles.

2. The Middleware (Node.js Server)
Acts as the orchestration layer, managing session states and utilizing Node's child_process module to safely trigger and manage Python-based machine learning scripts without thread-blocking.

3. The Local ML Pipeline (Python, yt-dlp, faster-whisper)
Optimized Audio Extraction: Uses yt-dlp to surgically extract audio streams without downloading full video payloads, drastically reducing network I/O.
Localized Automatic Speech Recognition (ASR): Utilizes faster-whisper (a highly optimized C++ implementation of OpenAI's Whisper model) to compute fast, highly accurate timestamps and text transcripts locally on the machine.

4. The Synthesis Engine (Gemini API & Streamlit)
Dynamic Algorithmic Prompting: Transcripts are fed into the Gemini API using specialized, zero-shot system instructions designed to classify content into three distinct analytical domains:
Political Content: Neutralizes partisan bias, emotional manipulation, and rhetorical fallacies.
Informative Content: Isolates verifiable assertions for cross-reference and automated fact-checking.
General Content: Injects crucial historical/cultural context missing from the baseline video.
Interactive Deep-Dive: If a user wants to audit the AI's conclusions, the state transitions smoothly into a localized Streamlit application, facilitating a stateful, 1-to-1 conversational Q&A session with the AI regarding the source data.

## Key Features ##
Real-Time De-biasing: Instant generation of a neutral summary stripped of algorithmic sensationalism.

Localized Sovereignty: High-privacy data pipeline—video parsing and transcription happen entirely on the user's local machine.

Cognitive Safety Net: Shifts user behavior from passive content consumption to active, dialectic cross-examination via the Streamlit chat portal.

## Installation and Usage Instructions ##
**example video of usage can be found at https://www.youtube.com/watch?v=APhDK69jBbI [MUTED]**

**another video of usage can be found at https://www.youtube.com/watch?v=7uPptG2c2-s [WITH VOICE]**

Because this project prioritizes user data sovereignty and circumvents centralized cloud storage, it runs entirely on a local infrastructure.

Prerequisites
Node.js (v16+)
Python (v3.8+)
A Gemini API Key set in your environment variables.

Step 1: Clone and Initialize Backend
git clone https://github.com/cosmic-perott/tmt-v3.git
cd tmt-v3

Install Node orchestration dependencies
npm install

Initialize the local API gateway
node server.js
(Note: Ensure your Python environment has dependencies installed via pip install faster-whisper yt-dlp streamlit google-generativeai).

Step 2: Load the Unpacked Browser Extension
Open Google Chrome and navigate to chrome://extensions/.

Enable Developer mode via the toggle in the upper-right corner.

Click Load unpacked in the upper-left corner.

Select the root folder of this repository

**For Best Performance, only click it once**

Once you have clicked the icon and the content has loaded, you will see an AI's response regarding the video's content.
This will include a neutralisation of biases and opinions (if it is a political video), fact checking (if it is an informative video), and providing additional information which would help users understand the content to a better degree(if the video does not fall into either category)

you can click on the entry box below and ask the AI follow up questions.
this will direct you to a website made with streamlit where you can have a 1 to 1 conversation with the AI about the given topic.


## Reflections on Project Made After Hackathon ##
Developing TMT under the intense constraints of a hackathon forced critical engineering trade-offs:

State Synchronization: Managing asynchronous state handshakes between a browser extension, a Node server, a Python script, and a separate Streamlit port required rigorous attention to error handling and race conditions.

Resource Management: Running local ASR models (faster-whisper) requires careful CPU/GPU allocation. Future iterations will include multi-threading optimization to prevent local server bottlenecks if multiple videos are processed concurrently.


***All architectural design, system integration, frontend/backend code, and documentation were conceived, structured, and authored end-to-end by cosmic-perott for the PennApps XXVI hackathon.***
