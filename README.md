# Mindmetrics-A-Full-Stack-ML-Powerhouse-Mental-Health-Awareness💙
We’re thrilled to share Mindmetrics, a full-stack machine learning web app built by Rani Soni and Rushikesh Gore, blending bleeding-edge ML, dual AI chatbots, and a stunning frontend to empower mental health insights. Check out the repo and dive into the code! 🚀
🔍 What’s Mindmetrics?

![main](https://github.com/user-attachments/assets/4fbe12f3-1cf3-464d-b667-ed8ea099e92f)

![screenshot-1745054447932](https://github.com/user-attachments/assets/33a3677b-15e0-4122-b830-27642d9c859d)

Mindmetrics predicts depression risk and analyzes personality through an engaging, responsive interface. Here’s how it works:
1. ML-Powered Depression Prediction 🧠

Core: A CatBoost 1.2 model, optimized with TensorFlow 2.15, processes 17 inputs (sleep, stress, diet, etc.) to predict depression risk, outputting a “Yes/No” result with probability (e.g., “32.5%”).

Backend: Served via FastAPI, it uses Pandas 2.2 for data pipelines and categorical encoding (e.g., “Female” → 0).

Frontend: Rushikesh’s result box, styled with red/green themes using Tailwind CSS 3.4, displays tips (e.g., “Try yoga” for high stress) and dynamic “Areas to Focus On” (e.g., “Add veggies” for unhealthy diets). A 3D loading GIF, served from AWS S3, enhances the UX.

Code Peek:
@app.post("/predict")
async def predict(data: dict):
    input_data = pd.DataFrame([data], columns=FEATURES)
    prob = model.predict_proba(input_data)[0][1]
    prediction = "Yes" if prob >= 0.5 else "No"
    return {"prediction": prediction, "probability": scale_probability(prob)}

![Screenshot_19-4-2025_15130_127 0 0 1](https://github.com/user-attachments/assets/5a9c4f49-8b48-44bf-89a7-f9e46c553d3e)

![Screenshot_19-4-2025_15056_127 0 0 1](https://github.com/user-attachments/assets/8f7c6ce7-28e2-4f44-9745-c41abcd69df9)

![Screenshot_19-4-2025_15020_127 0 0 1](https://github.com/user-attachments/assets/ea13cdda-ffd3-438f-9f0f-c4d1a322c640)

![Screenshot_19-4-2025_145740_127 0 0 1](https://github.com/user-attachments/assets/dac54dbd-8dd5-471f-a896-0dd852dc3684)

2. Dual AI Chatbot Personality Analysis 🤗

Chatbase.co-Powered Chatbot:

Trained on our dataset with LangChain for NLP, it handles Mindmetrics queries (e.g., “How does the app work?”).
Styled by Rushikesh with a heart.gif avatar in a React 18 interface, using Axios for API calls.


Custom Vibe Check Chatbot:

Runs a 9-question “Vibe Check” with:
Keystroke Analysis: Tracks typing speed (e.g., 49 chars/min) and question time (e.g., 2.8s) via WebSocket.
Emotion & Sentiment Detection: Uses BERT-based NLP to map keywords to emotions (happy, sad, stressed) and mood (positive, neutral), e.g., “Topped my exam” → “Pure joy! 🎉.”
Trait Mapping: Links responses to traits like “fun-loving 👫” or “dreamy 🚀” using custom Python logic (dictionaries like RESPONSE_TRAITS, arrays like userResponses).


WhatsApp-style UI features circular avatars (heart.gif for bot, icon.gif for user), gradient buttons, and a “Vibe Snapshot” report with stats (e.g., “9/9 questions, 14s total”).


Code Peek:
def analyze_personality(responses, durations):
    traits = []
    for resp in responses:
        for keyword, trait in RESPONSE_TRAITS.items():
            if keyword in resp.lower():
                traits.append(trait)
    return {"traits": traits, "stats": {"total_time": sum(durations)}}

![Screenshot_19-4-2025_145657_127 0 0 1](https://github.com/user-attachments/assets/3c1fdd72-c246-4481-a869-9be451e5c0ff)

![Screenshot_19-4-2025_145632_127 0 0 1](https://github.com/user-attachments/assets/ce81b863-9078-461e-804f-751e5b6294fe)

![Screenshot_19-4-2025_14562_127 0 0 1](https://github.com/user-attachments/assets/80476321-2bf2-4f45-b37d-83f3260d6d4f)

![Screenshot_19-4-2025_145510_127 0 0 1](https://github.com/user-attachments/assets/3cf5e49e-f735-4c19-8a9d-4d3362592fac)

![Screenshot_19-4-2025_15130_127 0 0 1](https://github.com/user-attachments/assets/fa5c68e4-9e2a-4d46-b44d-8acb40bcc89e)


3. Stunning Full-Stack Frontend ✨
Rushikesh’s frontend, built with React 18, Tailwind CSS 3.4, Three.js r165, and Framer Motion, includes:

800 animated stars and a 3D cube background via Three.js.

Multi-step forms with real-time validation and smooth progress bars.

Centered YES/NO buttons and gradient game option boxes with glow effects.

Responsive design with light/dark mode and a hamburger menu.

Code Peek:
const FormStep = ({ step }) => (
  <div className="form-step" style={{ display: step === currentStep ? 'block' : 'none' }}>
    <ProgressBar progress={step / TOTAL_STEPS * 100} />
    <ThreeJSBackground stars={800} />
  </div>
);

![Screenshot_19-4-2025_145446_127 0 0 1](https://github.com/user-attachments/assets/abaccd37-9de3-4634-8efb-0b2bf762caf5)

![Screenshot_19-4-2025_14548_127 0 0 1](https://github.com/user-attachments/assets/47d48d40-d62d-4530-b7a0-4a3d517081b7)

![Screenshot_19-4-2025_145345_127 0 0 1](https://github.com/user-attachments/assets/2d60389a-4e3e-459f-92fd-7e29e4856571)

![Screenshot_19-4-2025_14534_127 0 0 1](https://github.com/user-attachments/assets/be25fc78-76e8-4608-a742-1dac6fcfe1fb)


🛠 Cutting-Edge Tech Stack

Backend: Python 3.10, FastAPI for APIs, TensorFlow 2.15, Pandas 2.2, CatBoost 1.2, Loguru for logging.
Frontend: React 18 with Vite, Tailwind CSS 3.4, Three.js r165, JavaScript ES2023, Framer Motion for animations.
Chatbots: Chatbase.co API with LangChain for info chatbot, BERT for Vibe Check emotion detection, custom Python logic.
Infrastructure: Docker for containerization, Kubernetes for orchestration, WebSocket for real-time data, Redis for caching, AWS S3 for assets (e.g., pastel.gif, load.gif), fixed for 404s.
APIs & DevOps: AJAX with Axios and AbortController for 5s timeouts, GitHub Actions for CI/CD.
ML Pipeline: End-to-end training, hyperparameter tuning with Optuna, categorical encoding, containerized with Docker.

![Screenshot_19-4-2025_14520_127 0 0 1](https://github.com/user-attachments/assets/b01153bf-5d6d-4196-b573-9b782c4beb85)

![Screenshot_19-4-2025_145023_127 0 0 1](https://github.com/user-attachments/assets/c2a266e3-6da7-438a-b88c-8a930fc20a1f)

![Screenshot_19-4-2025_144929_127 0 0 1](https://github.com/user-attachments/assets/d4f4d58b-4da3-4b9d-9ee3-17964730fddd)

![Screenshot_19-4-2025_14716_127 0 0 1](https://github.com/user-attachments/assets/9a44f4f0-7c20-4938-91ed-161f4f517ced)

💡 Why It’s a Full-Stack ML Powerhouse
Mindmetrics integrates a CatBoost model with TensorFlow, a Kubernetes-orchestrated FastAPI backend, dual chatbots with BERT and LangChain, and a React-Three.js frontend, creating a scalable, engaging platform for mental health insights.
🙌 Team & Triumphs

![Screenshot_19-4-2025_14633_127 0 0 1](https://github.com/user-attachments/assets/45d22b50-ad12-47da-87c2-c470b7a61c06)

Rani Soni: Architected the full-stack ML pipeline, trained models, and built chatbot logic, including the custom Vibe Check.
Rushikesh Gore: Designed the stunning React-Tailwind frontend.
Chatbase.co: Enabled scalable info chatbot conversations.
Wins: Fixed button overlaps (z-index for send button, April 18, 2025), centered Vibe Snapshot with Tailwind (April 15, 2025), styled game options with gradients, and resolved 404s for assets like pastel.gif (April 18, 2025). Our literature survey drove tech choices like CatBoost and Three.js.

🚀 Get Involved
We’re exploring Grok 3 for advanced chatbot reasoning and MLflow for model tracking. Clone the repo, try Mindmetrics, and contribute! Open issues for bugs or feature ideas, or reach out for a tech chat. Let’s redefine mental health with code! 💬
#MentalHealth #FullStack #MachineLearning #Chatbot #Mindmetrics #Python #FastAPI #TensorFlow #React #OpenSource
