# AMD Finance Newsletter Generator

Automatically generates a weekly AMD finance newsletter PDF using the AMD LLM Gateway, covering:

- **AMD Financials & Earnings** — revenue, margins, segments, guidance
- **Global Gaming Market Trends** — Ryzen demand, Steam data, regional patterns
- **Competitor Analysis** — Intel vs AMD (CPU), Nvidia vs AMD (GPU/AI)

Each run produces a professionally formatted PDF saved to the `newsletters/` folder and pushed to your GitHub repo.

---

## Step 1 — Get an AMD LLM Gateway API Key

1. Open your web browser and go to [https://llm.amd.com/](https://llm.amd.com/)
2. Request an API key
3. Copy the key and keep it somewhere safe — you will need it in Step 7

> **Note:** You must be connected to the AMD internal network or VPN for the script to work.

---

## Step 2 — Create a GitHub Account (if you don't have one)

1. Go to [https://github.com](https://github.com)
2. Click **Sign up** and follow the steps to create a free account
3. Verify your email address

---

## Step 3 — Fork the repo

Forking creates your own personal copy of this project on GitHub.

1. Make sure you are logged in to GitHub
2. Go to [https://github.com/LucasbAMD/AI-Newsletter](https://github.com/LucasbAMD/AI-Newsletter)
3. Click the **Fork** button in the top-right corner of the page
4. On the next screen, click **Create fork**
5. GitHub will create your personal copy at `https://github.com/YOUR_USERNAME/AI-Newsletter`

---

## Step 4 — Install Git (if you don't have it)

Git is the tool that lets you download code from GitHub to your computer.

1. Go to [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Download and run the installer — click **Next** through all the default options
3. Once installed, continue to the next step

---

## Step 5 — Clone your fork to your computer

This downloads your forked repo to your laptop.

1. Press the **Windows key**, type `cmd`, and press **Enter** to open the Command Prompt
2. Navigate to where you want to save the project. For example, your Desktop:
```
cd %USERPROFILE%\Desktop
```
3. Type the following command, replacing `YOUR_USERNAME` with your GitHub username:
```
git clone https://github.com/YOUR_USERNAME/AI-Newsletter.git
```
4. Press **Enter** — Git will download the files. You should see a new folder called `AI-Newsletter`
5. Navigate into the folder:
```
cd AI-Newsletter
```

---

## Step 6 — Install Python and dependencies

**Install Python (if you don't have it):**
1. Go to [https://python.org/downloads](https://python.org/downloads) and download the latest version
2. Run the installer — make sure to check **"Add Python to PATH"** before clicking Install

**Install the required libraries:**

In your Command Prompt window, type:
```
pip install openai==1.101.0 gitpython reportlab python-dotenv
```
Press **Enter** and wait for it to finish — this may take a minute.

---

## Step 7 — Create your .env file

This is where your API key and folder path are stored. This file stays on your computer only and is **never uploaded to GitHub** — your API key is always safe.

1. Open File Explorer and navigate to your `AI-Newsletter` folder
2. Find the file called `.env.example`
3. Make a copy of it and rename the copy to `.env` (remove the word "example" entirely)
4. Right-click the `.env` file and open it with **Notepad**
5. You will see:
```
PROJECT_API_KEY=your-amd-gateway-key-here
REPO_PATH=C:/Users/YOUR_USERNAME/AI-Newsletter
```
6. Replace `your-amd-gateway-key-here` with your actual AMD LLM Gateway API key
7. Replace `YOUR_USERNAME` with your Windows username

   To find your Windows username: open File Explorer, click the address bar at the top of your `AI-Newsletter` folder — it will show the full path. Copy and paste it, but use forward slashes instead of backslashes.

   Example:
```
PROJECT_API_KEY=abc123yourkeyhere
REPO_PATH=C:/Users/johndoe/Desktop/AI-Newsletter
```
8. Save the file (Ctrl + S) and close Notepad

> **Important:** Never open or edit `generate_newsletter.py` to add your API key. Always use the `.env` file only.

---

## Step 8 — Run the script

1. Go back to your Command Prompt window (or open a new one, then type `cd %USERPROFILE%\Desktop\AI-Newsletter` and press Enter)
2. Type:
```
python generate_newsletter.py
```
3. Press **Enter**

The script will take a few minutes to run. You will see progress messages appearing. When it finishes you should see:
```
Done. Newsletter published to newsletters\amd_finance_newsletter_YYYY-MM-DD.pdf
```

Your newsletter PDF will automatically be pushed to your GitHub repo.

---

## Step 9 — View your newsletter on GitHub

1. Go to `https://github.com/YOUR_USERNAME/AI-Newsletter` in your browser
2. Click the `newsletters/` folder
3. Click the PDF file to download and open it

---

## What the newsletter contains

- TL;DR — a quick executive summary at the top
- Editor's Note
- AMD Financials & Earnings analysis
- Global Gaming Market Trends
- Competitor Analysis (Intel & Nvidia)
- Key Takeaways summary

---

## Troubleshooting

**`git` is not recognized**
Git is not installed. Go back to Step 4 and install it, then close and reopen your Command Prompt.

**`pip` is not recognized**
Python is not installed or not on your PATH. Go back to Step 6 and reinstall Python, making sure to check "Add Python to PATH".

**`PROJECT_API_KEY not found`**
Your `.env` file is missing or in the wrong place. Make sure it is named exactly `.env` (not `.env.example` or `.env.txt`) and is inside your `AI-Newsletter` folder.

**`REPO_PATH not set or folder does not exist`**
The path in your `.env` file is wrong. Open `.env` in Notepad, check the `REPO_PATH` line, and make sure it matches the actual location of your `AI-Newsletter` folder. Use forward slashes.

**`Connection error` when running the script**
You are not connected to the AMD internal network or VPN. Connect and try again.

**`Permission denied` on the PDF**
The newsletter PDF from a previous run is open in your PDF viewer. Close it and run the script again.
