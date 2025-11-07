📂 Project Structure
    DeepFakeDetection/
    ├── data/
    │   ├── raw/             # Downloaded videos 
    │   ├── processed/       # Extracted frames & faces
    │   └── manifests/       # CSVs mapping frames → labels
    │
    ├── notebooks/
    │   ├── 01_data_download.ipynb
    │   ├── 02_frame_extraction.ipynb
    │   ├── 03_train_cnn.ipynb
    │   └── 04_explainability.ipynb
    │
    ├── src/
    │   ├── preprocess.py    # Frame extraction & face detection
    │   ├── dataset.py       # Dataset loader
    │   ├── model.py         # CNN / LSTM models
    │   ├── train.py         # Training loop
    │   └── utils.py         # Helper functions
    │
    ├── requirements.txt
    ├── download.py
    ├── .gitignore
    └── README.md


⚙️ Installation
    1️⃣ Clone the Repository
        git clone https://github.com/<your-username>/DeepFakeDetection.git
        cd DeepFakeDetection

    2️⃣ Create Virtual Environment

    3️⃣ Install Dependencies
        pip install -r requirements.txt


📦 Dataset Setup
    This project uses a subset of the FaceForensics++ dataset (publicly available).

    1️⃣ Download Real and Fake Videos
    python download.py -d original -c c23 -t videos --num_videos 5 ./data/raw
    python download.py -d Deepfakes -c c23 -t videos --num_videos 5 ./data/raw

    2️⃣ Extract Frames and Faces
    After download, extract frames & faces:

    python src/preprocess.py


    This saves:

    data/processed/faces/<video_id>/*.jpg


    and generates a manifest CSV like:

    frame_path,label,video_id
    data/processed/faces/video_001/frame_0001.jpg,0,video_001
    data/processed/faces/video_002/frame_0001.jpg,1,video_002
