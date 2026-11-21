# Defense Presentation Script & Simple Term Guide (`02/`)

> **Deck:** [`Potato_Leaf_Disease_Defense_Slides.pptx`](Potato_Leaf_Disease_Defense_Slides.pptx) (35 slides) • [`Potato_Leaf_Disease_Defense_Slides.pdf`](Potato_Leaf_Disease_Defense_Slides.pdf)
> **Live App:** [https://potato.mamunlab.com/](https://potato.mamunlab.com/)
> **Note:** Every slide's short script and easy term guide below are also inside the PowerPoint **Speaker Notes** for Presenter View. For the full project glossary, see [Technical Glossary & Key Concepts](../../README.md#technical-glossary--key-concepts) in `README.md`.

---

## 5-Member Presenter Split (~11–12 Minutes + Live Demo & Q&A)

| Speaker | Slides | Topic | Time |
| :--- | :---: | :--- | :---: |
| **Speaker 1** | **Slides 1–8** | Intro, Team, Supervisor, Problem, 5 Classes, Goals | ~2.5 min |
| **Speaker 2** | **Slides 9–15** | Past Work, Dataset, Split, Pipeline, Our MobileNetV2 | ~2.5 min |
| **Speaker 3** | **Slides 16–23** | Training Gains, 4-Model Benchmark, Charts & Results | ~3.0 min |
| **Speaker 4** | **Slides 24–27** | Grad-CAM Heatmaps & Gemini AI Advice | ~2.0 min |
| **Speaker 5** | **Slides 28–35** | Live Web App, Impact, Conclusion, Future Work & Q&A | ~2.0 min |

### Quick Tips
- **Speak slowly and simply.** Don't read tables row by row—just share the main point.
- **Point to the screen** when talking about charts, heatmaps, and app screenshots.
- **Keep `https://potato.mamunlab.com/` open** in a browser tab with 2–3 leaf photos ready for the live demo.

---

## Slide-by-Slide Script & Simple Terms

---

### Slide 1 — Title Slide
*Speaker 1 • ~15s*

#### What to Say
> "Assalamu Alaikum and good morning/afternoon, respected panel members. Today we present our capstone project: **Explainable Deep Learning Based Potato Leaf Disease Detection and Intelligent Advisory System**. We built a small, accurate AI model that detects potato leaf diseases from real farm photos, shows why it decided, and gives farmers advice in English and Bengali."

#### Key Terms Explained
- **Explainable Deep Learning:** AI that does not just give an answer—it also shows *why* (here, with a heatmap on the leaf).
- **Advisory System:** An AI helper (Google Gemini) that explains the disease and gives safe next steps in plain language.

---

### Slide 2 — Our Team
*Speaker 1 • ~15s*

#### What to Say
> "Here is our five-member team from Intake 43, Section 02, Department of CSE at BUBT: Moniruzzaman, Tarikul Islam Sourov, Farhana Yeasmin, Jahangir Hossain Sohag, and Md. Al Mamun. Each of us will present one part of the project today."

#### Key Terms Explained
- *(Team slide — no technical terms.)*

---

### Slide 3 — Supervised By
*Speaker 1 • ~10s*

#### What to Say
> "We thank our supervisor, **Md. Sahiduzzaman**, Assistant Professor in the Department of Data Science and Engineering at BUBT, for his continuous guidance throughout this project."

#### Key Terms Explained
- *(Supervisor slide — no technical terms.)*

---

### Slide 4 — Overview
*Speaker 1 • ~15s*

#### What to Say
> "Here is our agenda. We will cover the problem, past work, our field dataset, our small MobileNetV2 model, our model comparison, Grad-CAM explainability, Gemini advice, and our live web app."

#### Key Terms Explained
- **Leak-Aware Split:** Keeping similar photos of the same leaf in the same group so test results stay honest.
- **Ablation Study:** Testing training tricks one by one on the same model to prove what improved accuracy.
- **Pareto Analysis:** Comparing both accuracy and file size together to find the best balance.

---

### Slide 5 — Introduction: Overview of Potato Leaf Disease
*Speaker 1 • ~20s*

#### What to Say
> "Potato is a major food crop in Bangladesh, but leaf diseases from fungi, bacteria, viruses, and *Phytophthora* cause heavy crop loss. When diseases are caught late or misread, leaves die, tubers rot, and farmers lose money on the wrong pesticides. Fast, accurate field detection is very important."

#### Key Terms Explained
- **Foliar Disease:** Any disease that attacks plant leaves.
- **Oomycete (*Phytophthora*):** A fast-spreading water-mold pathogen that causes Potato Late Blight.
- **Necrotic Lesion:** A brown or black spot of dead leaf tissue.
- **Chlorosis:** Yellowing of green leaves caused by stress or disease.
- **Tuber Rot:** Rotting of the potato underground.

---

### Slide 6 — Introduction: Five Biological Potato Leaf Classes
*Speaker 1 • ~25s*

#### What to Say
> "Our system detects five potato leaf classes. **Bacterial Disease** causes fast wilting and dark wet spots. **Fungal Disease**, like Early Blight, shows brown ring-shaped spots. **Healthy** leaves are clean and green. **Phytophthora**, or Late Blight, is the most dangerous and creates dark blotches that spread fast. **Viral Disease** causes yellow patches, curling, and weak growth."

#### Key Terms Explained
- **Early Blight:** A fungal disease with dark brown target-like rings on older leaves.
- **Late Blight (*Phytophthora*):** A dangerous, fast-spreading leaf blight that can wipe out a field quickly.
- **Mosaic Mottling:** Mixed light-green and yellow patches caused by a virus.

---

### Slide 7 — Motivations
*Speaker 1 • ~25s*

#### What to Say
> "Four problems drove our project. First, big models over 100 MB are too heavy for low-cost rural use—we need a small model under 10 MB. Second, lab datasets like PlantVillage use plain backgrounds and fail on real farms. Third, random data splits leak near-duplicate photos and fake high scores. Fourth, farmers need visual proof and simple Bengali and English advice, not just a label."

#### Key Terms Explained
- **PlantVillage:** A popular lab dataset with clean plain backgrounds; models trained only on it struggle outdoors.
- **Uncontrolled Field Imagery:** Real outdoor farm photos with soil, shadows, hands, and messy backgrounds.
- **Data Leakage:** When almost identical photos end up in both training and testing, inflating accuracy.
- **Ensemble Model:** Combining multiple neural networks together, which makes the file much larger.

---

### Slide 8 — Research Objectives
*Speaker 1 • ~25s*

#### What to Say
> "We set four clear goals. First, build a small, accurate **8.64 MB MobileNetV2** model for five potato leaf classes. Second, test it fairly against three bigger models on the exact same leak-free split. Third, check its focus using **Grad-CAM** heatmaps. Fourth, build a live English and Bengali web app with safe **Google Gemini** advice. Now my teammate will explain the literature, dataset, and model design."

#### Key Terms Explained
- **Parameters (2.26M):** The learned numbers inside a model; fewer parameters mean a smaller file.
- **MobileNetV2:** A fast, lightweight vision model built for phones and small servers.
- **Grad-CAM:** A heatmap tool that highlights which leaf areas the AI looked at.
- **FastAPI + React:** Our web stack—FastAPI runs the AI backend, and React builds the user website.

---

### Slide 9 — Literature Review – Comparative Table
*Speaker 2 • ~25s*

#### What to Say
> "Thank you. Older studies like Mohanty (2016) and Ferentinos (2018) got over 99% on clean PlantVillage lab photos using heavy models like VGG16, but accuracy drops to around 31% outdoors. Too et al. (2019) improved fine-tuning but still used large models with no farmer app. Shabrina et al. (2024) gave us real outdoor potato photos, but without Grad-CAM or an LLM web app. Our work brings all of these together in one **8.64 MB** model—**61 times smaller** than VGG16."

#### Key Terms Explained
- **VGG16 / ResNet / DenseNet:** Older, much heavier deep learning models (VGG16 has ~138M parameters vs. our 2.26M).
- **Fine-Tuning:** Updating a pretrained model on our potato leaves instead of training from scratch.
- **Domain Shift:** Accuracy dropping when a lab-trained model sees real outdoor farm photos.

---

### Slide 10 — Dataset
*Speaker 2 • ~25s*

#### What to Say
> "Our dataset on Kaggle (`potato-disease-dataset-03`) has **2,321 real outdoor photos** across five classes—taken with soil, mulch, shadows, and overlapping leaves. Fungal is the largest class with 729 photos, and Healthy is the smallest with 199. Before splitting, we ran **`dHash <= 10`** to find **38 near-duplicate clusters**, grouping the photos into **2,283 unique leaf groups** so matching photos never split across train and test."

#### Key Terms Explained
- **`dHash` (Difference Hash):** A 64-bit visual fingerprint that catches nearly identical or slightly cropped photos.
- **Hamming Distance (`<= 10`):** How many fingerprint bits differ; `<= 10` means two photos look almost the same.
- **Class Imbalance:** Some classes have more photos than others (729 Fungal vs. 199 Healthy).

---

### Slide 11 — Dataset Split Overview
*Speaker 2 • ~20s*

#### What to Say
> "From those 2,283 groups, we made a clean **80 / 10 / 10 split** using `StratifiedGroupKFold` with seed 42: **1,859 train, 231 validation, and 231 test images**. All four models used this exact same split for a fair test. We also used **class weights** so smaller classes like Healthy (weight 1.89) and Phytophthora (1.22) were not ignored."

#### Key Terms Explained
- **`StratifiedGroupKFold`:** Keeps class ratios balanced across splits while keeping duplicate groups together.
- **Train / Validation / Test:** Train teaches the model; Validation picks the best settings; Test gives the final unbiased score.
- **Class Weights:** Gives extra importance to smaller classes during training so the model learns them well.

---

### Slide 12 — Methodology
*Speaker 2 • ~25s*

#### What to Say
> "Here is our five-step pipeline. Step 1 cleans the dataset and makes the leak-free 80/10/10 split. Step 2 resizes images to `224×224`, rescales pixels, and adds data augmentation like flips, zoom, and brightness changes. Step 3 trains our MobileNetV2 and three benchmark models. Step 4 checks test accuracy, 4-view TTA, export parity, and Grad-CAM heatmaps. Step 5 deploys everything into our live web app with Gemini advice."

#### Key Terms Explained
- **Data Augmentation:** Creating rotated, flipped, or brighter versions of training photos so the AI handles real farm conditions.
- **Native Rescaling (`[-1, 1]`):** Built-in pixel scaling inside the saved model so training and web serving match 100%.
- **4-View TTA:** Testing a leaf in 4 flipped views and averaging the predictions for better accuracy.

---

### Slide 13 — Proposed Compact Model (MobileNetV2)
*Speaker 2 • ~25s*

#### What to Say
> "Our Proposed MobileNetV2 is only **8.64 MB** with **2.26 million parameters**. Instead of a heavy classifier head that overfits on 1,859 images, we used a tiny head: Global Average Pooling, 0.25 Dropout, and a 5-class Softmax layer—just **6,405 head parameters**. We trained in two stages: first we trained only the head and restored its best Epoch-6 weights; then we unfroze the top 54 layers while keeping **all BatchNorm layers frozen**, using **AdamW** and label smoothing."

#### Key Terms Explained
- **Global Average Pooling (GAP):** Compresses each feature map into one average number, preventing overfitting.
- **Dropout (`0.25`):** Randomly turns off 25% of neurons during training so the model generalizes better.
- **Softmax:** Turns raw model outputs into percentages for the 5 classes that add up to 100%.
- **Frozen BatchNorm:** Keeping ImageNet normalization stats locked during Stage 2 so training stays smooth and stable.
- **AdamW:** An optimizer that prevents overfitting better than regular Adam.
- **Label Smoothing (`0.05`):** Stops the model from becoming overly confident during training.

---

### Slide 14 — Proposed Explainable CNN Design
*Speaker 2 • ~25s*

#### What to Say
> "This slide shows how our Explainable CNN works in three parts. **What it does:** takes a `224×224` leaf photo and outputs 5-class scores plus a Grad-CAM heatmap from `Conv_1`. **Why we use it:** MobileNetV2 gives top accuracy at just 8.64 MB—13.7 times smaller than MultiNet-V3—while GAP and frozen BatchNorm keep it stable. **Where it lives:** inside our FastAPI server as a verified `.keras` file with zero numerical drift (`0.00e+00`), sending only text labels to Gemini."

#### Key Terms Explained
- **Depthwise Separable Convolution:** A smart lightweight filter that makes MobileNetV2 small and fast.
- **`Conv_1` Layer:** The last spatial feature layer (`7×7×1280`) in MobileNetV2, used to draw Grad-CAM heatmaps.
- **Serving Parity (`0.00e+00`):** Proves the saved production model gives the exact same outputs as training.

---

### Slide 15 — Proposed MobileNetV2 Layer Configuration
*Speaker 2 • ~20s*

#### What to Say
> "Here is the exact layer structure of our saved model. A `224×224×3` photo goes through built-in Rescaling, the 154-layer MobileNetV2 backbone (2.26M params), Global Average Pooling, 0.25 Dropout, and our 5-class Softmax layer (6,405 params). Total size: **2,264,389 parameters**, or **8.64 MB**. Now my teammate will share our results and model comparisons."

#### Key Terms Explained
- **Output Shape (`7×7×1280`):** A `7×7` spatial grid with `1,280` learned visual features (spots, edges, yellowing).
- **36 Non-BN Layers:** Inside the top 54 layers, 18 BatchNorm layers stay frozen and 36 layers learn new leaf features.

---

### Slide 16 — Training Optimization Ablation (Zero Size Cost)
*Speaker 3 • ~30s*

#### What to Say
> "Thank you. First, we tested how much better training helps the **exact same 8.64 MB file**—zero extra size. Our baseline MobileNetV2 used Adam and unfrozen BatchNorm, which caused a big loss spike at Epoch 9 (`0.83` up to `2.63`) and stopped at **91.34%** accuracy. When we froze BatchNorm, restored the best Stage-1 head, used AdamW, and unfroze 54 layers, the spike disappeared. Accuracy jumped to **93.51%**, test loss dropped by **33.6%**, and Phytophthora recall jumped from **81% to 94%**. Adding 4-view TTA pushed accuracy to **93.94%**."

#### Key Terms Explained
- **Fine-Tuning Shock:** A sudden jump in error right after unfreezing backbone layers.
- **Test Loss:** Measures how confident and accurate the probability scores are (lower is better).
- **Early Stopping (`ES`):** Stops training automatically once validation score stops improving, preventing overfitting.

---

### Slide 17 — Comparative Benchmark Architectures
*Speaker 3 • ~25s*

#### What to Say
> "Next, we compared our small model fairly against three larger architectures on Kaggle dual T4 GPUs using the exact same `1,859 / 231 / 231` split and seed 42. We tested **Proposed MobileNetV2** (8.64 MB), **NASNetMobile** (17.33 MB), **InceptionV3** (85.18 MB at `299×299`), and **MultiNet-V3 Ensemble** (118.55 MB combining three backbones). Every saved model passed the `0.00e+00` reload check."

#### Key Terms Explained
- **`MirroredStrategy`:** Runs training in parallel across two GPUs at the same time.
- **NASNetMobile:** A compact model designed by Google's automated architecture search (`17.33 MB`).
- **InceptionV3:** A larger multi-scale CNN using higher-resolution `299×299` inputs (`85.18 MB`).
- **MultiNet-V3 Ensemble:** Combines EfficientNetB0, MobileNetV2, and ResNet50 together (`118.55 MB`).

---

### Slide 18 — Result (Proposed MobileNetV2)
*Speaker 3 • ~25s*

#### What to Say
> "These three graphs show our MobileNetV2 training history: Accuracy, Loss, and Validation Macro-F1. Right after Epoch 10 when Stage 2 starts, there is **no loss spike**—training stays smooth. Validation Macro-F1 peaks at **0.9184** at Epoch 33 and stops cleanly at Epoch 45. On the unseen 231 test images, this model reaches **93.51%** single-pass and **93.94%** with 4-view TTA."

#### Key Terms Explained
- **Training vs. Validation Curves:** When both lines stay close together, the model is learning well without overfitting.
- **Macro-F1:** Average F1 score giving all 5 classes equal weight, even smaller ones.
- **Chance Line (`0.20`):** What random guessing across 5 classes would score (20%).

---

### Slide 19 — Confusion Matrix (Proposed MobileNetV2)
*Speaker 3 • ~25s*

#### What to Say
> "On our 231 unseen test leaves, our model got **216 right**. **Bacterial Disease** got **54 out of 54** (100% recall). **Healthy** got **19 out of 19** (100% recall). High-risk **Phytophthora** got **29 out of 31** (94% recall). **Viral** got **50 out of 53**, and **Fungal** got **64 out of 74**—with only a few subtle early-stage spots mixed up with Healthy or Phytophthora."

#### Key Terms Explained
- **Confusion Matrix:** A table showing true labels (rows) vs. predicted labels (columns); the diagonal shows correct answers.
- **Recall:** Out of all real cases of a disease, how many the model caught.
- **Precision:** Out of all leaves predicted as a class, how many were actually right.

---

### Slide 20 — Classification Report (Test Set, N = 231)
*Speaker 3 • ~20s*

#### What to Say
> "Here are the full test scores for every class. Every class reaches **0.88 F1 or higher**: Bacterial 0.99, Viral 0.96, Fungal 0.91, Phytophthora 0.89, and Healthy 0.88. Healthy precision is 0.79 simply because it only has 19 test photos and 5 mild fungal leaves looked Healthy. Overall, we reach **93.51% accuracy** and **0.9272 Macro-F1**."

#### Key Terms Explained
- **F1-Score:** One balanced score combining Precision and Recall (from 0 to 1; higher is better).
- **Macro vs. Weighted Average:** Macro treats every class equally; Weighted counts larger classes more.
- **Support:** How many test photos belong to each class (231 total).

---

### Slide 21 — Model Comparison – Master Benchmark Table
*Speaker 3 • ~30s*

#### What to Say
> "This table is our main finding. Our **8.64 MB MobileNetV2** sits alone on **Pareto Front 1**—it is both the **smallest** and the **most accurate** model at **93.51%** single-pass and **93.94%** TTA. The **118.55 MB MultiNet-V3 Ensemble** is **13.7 times larger**, yet scores lower at **90.91%**. InceptionV3 scores **84.42%**, and NASNetMobile scores **72.73%**. Our efficiency score (`0.995`) is more than double the heavy models."

#### Key Terms Explained
- **Pareto Front 1:** No other model is both smaller and more accurate—our model wins on both.
- **Efficiency (`F1 / log10 MB`):** Measures how much accuracy a model gets per unit of storage size.
- **Why Bigger Models Lost:** On 1,859 farm photos, huge 22M–31M models overfit background clutter faster than our lean 2.26M model.

---

### Slide 22 — Model Comparison (Overall & Per-Class Charts)
*Speaker 3 • ~20s*

#### What to Say
> "These charts make the gap clear. On the left, MobileNetV2 leads in both Accuracy and Macro-F1. On the right per-class heatmap, MobileNetV2 **wins or ties on all five disease classes**. No heavier model beats it on even a single class."

#### Key Terms Explained
- **Per-Class Heatmap:** Darker blue means a higher F1 score; shows our model is strong across every class, not just one.

---

### Slide 23 — Model Comparison – Accuracy vs. Model Size
*Speaker 3 • ~20s*

#### What to Say
> "This scatter plot shows size on the bottom and Macro-F1 on the side. The best spot is the **top-left corner**—smallest file and highest score. Our MobileNetV2 sits there alone, while all three bigger models fall in the shaded dominated zone. Smart training beats sheer model size. Now my teammate will present Grad-CAM explainability and Gemini advice."

#### Key Terms Explained
- **Log Scale:** Compresses big size jumps (10 MB to 100 MB) so small and large models fit clearly on one chart.
- **Dominated Region:** Area where models are worse on both goals—bigger file size AND lower accuracy.

---

### Slide 24 — Explainable AI (Grad-CAM Validation)
*Speaker 4 • ~30s*

#### What to Say
> "Thank you. High accuracy is not enough—we must prove the AI looks at the leaf, not the soil. Using Grad-CAM on `Conv_1`: in the middle row (**Fungal, 97.4%**), red heat locks onto the brown spots and ignores the plastic sheet. In the bottom row (**Bacterial, 99.1%**), it focuses on the wilted leaf and ignores the hand. In the top row—a harder **66.7%** error case—the heatmap drifts off the leaf, giving a clear visual warning to double-check with an expert."

#### Key Terms Explained
- **Grad-CAM Overlay:** Colors the image to show AI focus—red/yellow means high attention, blue means ignored.
- **Shortcut Learning:** When an AI cheats by looking at background soil or hands instead of real disease spots.
- **Error Transparency:** Low confidence plus an off-leaf heatmap warns the farmer not to blindly trust the result.

---

### Slide 25 — LLM Integration (Pipeline Diagram)
*Speaker 4 • ~20s*

#### What to Say
> "A disease name alone is not enough for a farmer. Here is our safe advisory pipeline: first, MobileNetV2 predicts the disease locally from the photo. Then, **only the disease name and confidence**—never the raw photo—go to our Prompt Builder and **Google Gemini (`gemini-3.1-flash-lite`)**, which returns simple, safe advice."

#### Key Terms Explained
- **Decoupled Pipeline:** The CNN handles image vision and the LLM handles plain-language advice—each does what it is best at.
- **Prompt Builder:** Adds strict safety rules and formatting before calling Gemini.
- **Text-Only Handoff:** Keeps farmer photos private on our server and makes API calls fast and cheap.

---

### Slide 26 — LLM Integration (Model & Engineering Details)
*Speaker 4 • ~25s*

#### What to Say
> "We use **`gemini-3.1-flash-lite`** via Google's official **`google-genai`** Python SDK, with our API key safely stored in environment variables. MobileNetV2 predicts the class and Grad-CAM; Gemini receives only the label and confidence and replies in **English or Bengali** with symptoms, care steps, and prevention. Strict **safety rules** block invented pesticide brands or dosages and suggest local agriculture officers when confidence is low."

#### Key Terms Explained
- **`gemini-3.1-flash-lite`:** Fast, lightweight Google Gemini model ideal for quick bilingual farmer advice.
- **Safety Guardrails:** Rules that stop the AI from inventing risky chemical dosages or brand names.
- **Secret Handling:** Keeping API keys in server settings instead of source code so they never leak.

---

### Slide 27 — Expanded LLM-Based Advisory Output
*Speaker 4 • ~25s*

#### What to Say
> "Our advice follows four clear steps: **CNN Result**, **Explanation**, **Action Guidance**, and **Prevention**. Here is a real example from our app: **Fungal Disease at 100% confidence**. It explains brown ring spots and suggests safe field steps like removing badly infected lower leaves, improving airflow, and avoiding evening overhead watering—in English or Bengali, with zero invented chemical doses. Now my teammate will show our live web app and wrap up."

#### Key Terms Explained
- **Cultural Management:** Safe non-chemical farm steps like pruning dead leaves, better spacing, and careful watering.
- **Agricultural Extension Officer:** Local government farming experts who confirm field cases and approved treatments.

---

### Slide 28 — Implementation (Web App Demo)
*Speaker 5 • ~25s*

#### What to Say
> "Thank you. We deployed the full system live at **`https://potato.mamunlab.com/`** using **FastAPI**, our **8.64 MB MobileNetV2**, **React**, and **Docker**. Farmers can upload a photo or use their phone camera to get instant 5-class results, Grad-CAM heatmaps, **12-leaf batch checks with CSV export**, **PDF reports**, Disease Info cards, and **English/Bengali AI chat**."

#### Key Terms Explained
- **FastAPI:** Fast Python backend that runs the model, Grad-CAM, and Gemini API.
- **React + TypeScript:** Frontend website that works smoothly on any phone browser without installing an app.
- **Docker Compose + Traefik:** Runs the whole app reliably with automatic HTTPS security.

---

### Slide 29 — Web App Demo – Detection & Grad-CAM Results
*Speaker 5 • ~20s*

#### What to Say
> "Here are two real screens from our live app. On the left, farmers can drag-and-drop a photo or tap **Take a photo** on their phone. On the right, the result shows **Fungal Disease at 100.0% confidence**, the **Original leaf** next to the **Grad-CAM heatmap**, and one-click buttons to **Ask AI**, read **Disease Info**, or download a **PDF report**."

#### Key Terms Explained
- **Non-Clinical Disclaimer:** A clear notice telling users this is AI screening support, not a final lab diagnosis.

---

### Slide 30 — Web App Demo – Batch Analysis & Bilingual AI Chat
*Speaker 5 • ~25s*

#### What to Say
> "Here are two features built for field scouting and farmers. On the left, **Batch Analysis** scans up to **12 leaves at once**—here showing 1 Healthy and 3 Diseased leaves with Top-3 probabilities and one-click **CSV download**. On the right, our **AI Assistant** already knows the detected disease, answers follow-up questions in **English or Bengali**, and gives safe action steps."

#### Key Terms Explained
- **Batch Analysis:** Checks up to 12 farm photos in one go for field scouts and exports a CSV sheet.
- **Context-Seeded Chat:** Automatically shares the detected disease with Gemini so farmers don't have to retype it.

---

### Slide 31 — User Benefits & Real-World Impact
*Speaker 5 • ~20s*

#### What to Say
> "In short, our system gives farmers five real benefits: **instant results** on any phone, **visual Grad-CAM proof** that builds trust, **plain English and Bengali advice**, **12-leaf batch scouting** with CSV and PDF reports, and an **8.64 MB compact model** that runs fast on low-cost servers and is ready for offline phones."

#### Key Terms Explained
- **Edge-Ready Model:** Small enough (`8.64 MB`) to run cheaply on basic servers or directly on budget Android phones.

---

### Slide 32 — Conclusion
*Speaker 5 • ~25s*

#### What to Say
> "To conclude, we met all four goals. We built an **8.64 MB MobileNetV2** reaching **93.51%** single-pass and **93.94%** TTA accuracy on real outdoor potato leaves. It beat much bigger models—including a **13.7× larger MultiNet-V3 ensemble**—on the exact same leak-free test split. We verified lesion focus with **Grad-CAM** and `0.00e+00` export accuracy, and launched our live bilingual web app at **`https://potato.mamunlab.com/`**."

#### Key Terms Explained
- **Reproducibility:** Fixed seeds and saved notebooks mean anyone can re-run our work and get the same results.

---

### Slide 33 — Future Work
*Speaker 5 • ~20s*

#### What to Say
> "Next, we plan four upgrades. First, shrink our model to **~2.5 MB INT8 TFLite** for a 100% **offline Android app**. Second, collect more local potato photos across **Bogura, Munshiganj, and Rangpur** with local agronomists. Third, expand to **tomato, rice, and wheat**. Fourth, add true **disease severity scoring** and **humidity-based Late Blight alerts**."

#### Key Terms Explained
- **INT8 Quantization (TFLite):** Shrinks model weights from 32-bit to 8-bit (`8.64 MB -> ~2.5 MB`) for fast offline phone use.
- **Lesion Segmentation:** Measures the exact pixel area of disease spots to give a true severity percentage.

---

### Slide 34 — References
*Speaker 5 • ~10s*

#### What to Say
> "Here are the key research papers behind our dataset, models, and Grad-CAM method. Full IEEE references are in our thesis report."

#### Key Terms Explained
- **IEEE Citation Style:** Numbered citations (`[1]`, `[2]`, ...) standard in engineering reports.

---

### Slide 35 — Closing / Q&A & Live Demo
*Speaker 5 • ~10s*

#### What to Say
> "Thank you very much for your time. We are happy to answer your questions and show a quick live demo at **`https://potato.mamunlab.com/`**."

#### Key Terms Explained
- *(Closing slide — move to live demo or Q&A below.)*

---

## Quick Panel Q&A Cheat Sheet (Simple Answers)

| Likely Question | Short, Easy Spoken Answer |
| :--- | :--- |
| **1. How did an 8.64 MB MobileNetV2 beat a 118.55 MB ensemble?** | *"On 1,859 farm photos, huge 31M-parameter models overfit background noise quickly. Our small 2.26M model with a tiny head, frozen BatchNorm, and AdamW generalized much better without overfitting."* |
| **2. Why did you freeze BatchNorm in Stage 2?** | *"Unfreezing BatchNorm on a small dataset messes up its stable ImageNet statistics—causing the big Epoch-9 loss spike (`0.83 -> 2.63`) we saw in our baseline. Freezing it removed the spike and cut test loss by 33.6%."* |
| **3. Why use `dHash <= 10` instead of a normal random split?** | *"Farm datasets often have burst shots of the same leaf. A random split puts the same leaf in both train and test and fakes high accuracy. `dHash <= 10` grouped 38 duplicate clusters so testing stays 100% honest."* |
| **4. Why is Healthy precision 0.79 when recall is 100%?** | *"We got all 19 Healthy leaves right, and 5 very mild Fungal leaves were predicted as Healthy. Because Healthy only has 19 test photos, just 5 mistakes drop precision to 79%. Collecting more Healthy photos is our top data goal."* |
| **5. Why 5 classes now instead of 7 in Phase 01?** | *"In Phase 01, Nematode had only 68 photos (huge imbalance) and Pest is insect damage, not a biological disease. Phase 02 focuses on the 5 core disease/healthy classes with full GPU transfer learning and benchmarking."* |
| **6. How does 4-View TTA improve accuracy with zero extra size?** | *"We run the exact same 8.64 MB model on 4 flipped views of the leaf and average the scores. Since leaves have no fixed top or bottom, averaging boosts accuracy from 93.51% to 93.94% with zero added weights."* |
| **7. What does `0.00e+00` serving parity mean?** | *"It means we reloaded every saved `.keras` file outside multi-GPU training and confirmed zero numerical difference (`0.00e+00`) in predictions—so the web app matches our Kaggle results 100%."* |
| **8. Why not send the leaf photo directly to Gemini?** | *"Three reasons: privacy (photos stay on our server), accuracy (our specialized CNN gives tested scores and Grad-CAM), and speed/cost (text-only prompts are much faster and cheaper)."* |
| **9. What if someone uploads a non-leaf photo (like a car)?** | *"Right now, a 5-class Softmax model always picks one of the 5 classes, though strange photos usually get lower confidence and messy Grad-CAM maps. Adding a non-leaf rejection check is part of our roadmap."* |
| **10. Does the app work offline in villages right now?** | *"Right now it is a live web app needing basic 3G/4G data, with no app install needed. Because our model is already just 8.64 MB, our #1 next step is converting it to a ~2.5 MB offline Android TFLite app."* |
