
# Web UI-Thanks to BrowserUSE
This project is focused on automating browser tasks using an AI agent. Specifically, it enables intelligent web interactions such as filling out and submitting job applications automatically. It leverages browser automation with Playwright and AI-driven decision-making to streamline repetitive workflows.

![Web UI Demo](https://github.com/AloysJehwin/web-ui/blob/main/assets/Screenshot%202025-06-06%20002918.png)

Here we are using the AI Agent for job application automation but this can be used for many more!
![Web UI Demo](https://github.com/AloysJehwin/web-ui/blob/main/assets/Screenshot%202025-06-06%20003151.png)

## Installation

### Step 1: Clone the Repository
```bash
git clone https://github.com/AloysJehwin/web-ui.git
cd web-ui
````

### Step 2: Set Up Python Environment (using uv)

```bash
uv venv --python 3.11

# Activate the virtual environment (Command Prompt)
.venv\Scripts\activate

# Or using PowerShell
.\.venv\Scripts\Activate.ps1
```

### Step 3: Install Dependencies

```bash
uv pip install -r requirements.txt

# Install Playwright with all browser dependencies
playwright install --with-deps

# Or install only Chromium browser
playwright install chromium --with-deps
```

### Step 4: Configure Environment

```bash
copy .env.example .env
```

Open `.env` in your preferred text editor and add your API keys and other configuration settings.

### Step 5: Set Up AI API Access

To enable AI-powered automation, you need an API key from an AI provider.

An example `.env.example` file is provided to guide you with the required environment variables. Make sure to duplicate and modify it as shown in the previous step.

We recommend exploring [OpenRouter](https://openrouter.ai/) which offers free and paid access to multiple AI models.

After signing up, obtain your API key and add it to the `.env` file:

```
OPENROUTER_API_KEY=your-api-key-here
```

### Step 6: Run the Web UI

```bash
python webui.py --ip 127.0.0.1 --port 7788
```

![Automation Demo](https://github.com/AloysJehwin/web-ui/blob/main/assets/Screenshot%202025-06-06%20004500.png)

## Customize Your Automation

You can automate web processes in your own way using a well-written prompt that describes your goal clearly.

Here’s an example prompt to automate job applications on LinkedIn using an AI agent:

```yaml
instructions:
  goal: "Automatically apply to all LinkedIn jobs that support 'Easy Apply' for Aloys Jehwin using the highlighted resume, skipping optional fields, and answering required fields just as shown in the video."
  steps:
    - Go to: "https://www.linkedin.com/jobs/search/?f_AL=true&keywords=software%20engineer"
    - For each job listing:
        - Click on the job to open its detail panel.
        - Wait for the job panel to fully load.
        - Check for the 'Easy Apply' button.
        - If **'Easy Apply' is not visible**, skip this job and move to the next.
        - If **'Easy Apply' is present**:
            - Click the 'Easy Apply' button.
            - Use the **already highlighted resume** (do NOT upload a new one).
            - Proceed through each step of the application:
                - If a field is **already filled**, leave it untouched.
                - If a field is **required and empty**, fill as follows:
                    - Full Name: Aloys Jehwin
                    - Email: aloysjehwin@gmail.com
                    - Phone: +91 94892 54099
                    - Location: Chennai, Tamil Nadu, India
                    - Experience: 1 year
                    - Notice Period: 15 days
                    - Current CTC: 456000
                    - Expected CTC: 900000
                - Skip all optional fields including:
                    - Message to Hiring Manager
                    - Additional attachments
                    - Cover letters
            - If the form has multiple steps:
                - Click 'Next' on each step, filling only **mandatory and empty** fields.
            - If the **'Submit application'** button is not visible:
                - Scroll down slightly to reveal it.
            - Once visible, click **'Submit application'**.
            - If a **'Done' or confirmation** button appears after submission:
                - Click it to complete and return to the job list.
        - Immediately move to the next job and repeat the process.

files:
  - Use the **highlighted resume already on LinkedIn** (do not upload or replace).

notes:
  - Apply to **every job that has Easy Apply**, regardless of job title or priority.
  - Do not overwrite any field already filled.
  - Do not write or attach custom messages.
  - Finish the current page fully before stopping.
```

## Tech Stack

* Python 3.11
* Playwright
* uv (Python environment manager)

## Project Structure

```
web-ui/
├── src/
├── .env.example
├── requirements.txt
├── webui.py
├── README.md
```

## Contributing

1. Fork the repository
2. Create a new branch (`git checkout -b feature-name`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature-name`)
5. Open a Pull Request

## Reporting Issues

If you encounter bugs, please open an issue with steps to reproduce and expected vs. actual behavior.

## License

This project is licensed under the [MIT License](LICENSE).
