Clean Audio Player & Censor Pipeline 🎧✨

An automated profanity-filtering player and transcription pipeline designed for long-form audiobooks (including multi-hour .m4b and .mp3 files).

The web player runs client-side in the browser via GitHub Pages, muting explicit words and skipping scenes dynamically based on a timestamped JSON filter map.

🚀 Quick Links

Audiobook Scanner Notebook (Google Colab): [Launch Colab Scanner Notebook](https://colab.research.google.com/drive/1MKMrkkg6SqoGvEL5UD7MV79Iv54CP0Bt?usp=sharing)

📖 How It Works

Scan: An audiobook file is processed through Faster-Whisper on a free Google Colab T4 GPU. The script scans every spoken word, matches vulgarities against an expletive blocklist, and outputs a lightweight censor_map.json file.

Deploy: The censor_map.json is stored in the repository root alongside the web player.

Listen: The listener opens the web player, selects their local audiobook file, and enjoys automated, synchronized audio muting with zero audio latency.

🛠️ Step-by-Step Guide for Creating a New Censor Map

Anyone can create a censor map for their own audiobook by running our automated Colab notebook:

1. Open and Set Up the Notebook

Open the Google Colab Notebook.

Click File > Save a copy in Drive to save your personal working copy.

Verify your runtime has GPU acceleration enabled:

Go to Runtime > Change runtime type.

Under Hardware accelerator, select T4 GPU and click Save.

2. Prepare the Audiobook

Run the first cell in the notebook by clicking the Play (▶) button.

Follow the prompt to connect and authorize your Google Drive.

The script will automatically create a folder in your Drive called:

Google Drive / CleanAudioBooks


Upload your audiobook (.m4b or .mp3) directly into that CleanAudioBooks folder.

3. Run the Scan

Re-run the Colab cell.

The notebook will automatically:

Isolate the raw audio track and bypass embedded chapter markers/cover art.

Segment the file into 30-minute processing chunks.

Run Faster-Whisper with word-level precision.

Export <AudiobookName>_censor_map.json directly back into your Google Drive folder.
(A standard 12-hour audiobook finishes in roughly 35–45 minutes).

📱 Hosting the Audiobook in Your Player

Loading the Map into GitHub Pages

Download the generated _censor_map.json from your Google Drive.

Rename the file to censor_map.json.

Upload and commit censor_map.json into the root directory of this GitHub repository.

GitHub Pages will automatically update in seconds.

Playing the Audiobook

Open the web app on your phone or desktop:
https://<YOUR-GITHUB-USERNAME>.github.io/<YOUR-REPO-NAME>/

The app will automatically fetch and load censor_map.json in the background.

Tap Select Audiobook and choose your matching audio file from your device.

Hit Play. The player will mute expletives and display real-time statuses.

⚙️ Features of the Web Player (v3.0)

Mobile First & PWA Compatible: Installable directly to your phone's home screen.

Landscape Mode Support: Dynamic layout adaptation when rotating horizontal or vertical.

Large Scrub Bar: High-visibility timeline slider with ±30-second jump controls.

Local File Execution: Audio files are played locally in the browser memory via Object URLs—no multi-gigabyte audio uploads needed.

Configurable Filters: Toggle switches to enable or disable word mutes and scene skips independently.

🔒 Privacy & Local Processing

Audio playback is 100% private and stays entirely on the local device. The audio file is never uploaded to GitHub or third-party web servers.

The transcription script in Google Colab runs within your own Google account storage.
