### 1. Install Required Python Packages

Run the following command in your terminal or command prompt to install the necessary libraries for the Telegram bot interface:

```bash
pip install python-telegram-bot httpx

```

Copy Command

### 2. Configure API and Identity Keys

Open your local `lock_workstation.py` file and update the configuration variables with your authorization tokens:

```python
# Line 9: Replace with the token provided by @BotFather
BOT_TOKEN = "YOUR_TELEGRAM_BOT_TOKEN"

# Line 13: Replace with your specific numerical Telegram Chat ID (Do not use quotes)
ALLOWED_CHAT_ID = ""

# Line 17: Update to point to the exact absolute path where this file resides
LOCK_SCRIPT_PATH = r"C:\Users\<Your-Username>\PycharmProjects\telegram\lock_workstation.py"

```

### 3. Deploy Background Task via PowerShell

To automate background execution on system startup without a lingering command prompt window, register the XML definition using an elevated PowerShell window:

```powershell
Register-ScheduledTask -Xml (Get-Content ".\telegram_bot_trigger.xml" -Raw) -TaskName "TelegramBot_AutoRun" -Force

```

Copy PowerShell Command

### 4. Path Validation in Windows Task Scheduler

1. Press `Win + R`, type `taskschd.msc`, and press Enter.
2. Select the **Task Scheduler Library** folder and locate **TelegramBot_AutoRun**.
3. Right-click the task, click **Properties**, and navigate to the **Actions** tab.
4. Click **Edit** on the existing action and modify the target references:
* **Program/script:** Verify this points directly to your Python executable (e.g., `C:\Users\<Your-User>\AppData\Local\Programs\Python\Python313\python.exe`).
* **Add arguments (optional):** Set this to the absolute file path of your execution script (e.g., `C:\Users\<Your-User>\PycharmProjects\telegram\lock_workstation.py`).


5. Click **OK** and save the modifications. Right-click the task and select **Run** to launch the initialization sequence instantly.
