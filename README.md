# 🚀 RDP2-247 Master Control (Repo: RDP2)

This repository manages two additional parallel Windows RDP nodes (**RDP2-Alpha** and **RDP2-Bravo**) running 24/7 via GitHub Actions and Tailscale.

## 📊 Connection Details
- **User:** `runneradmin`
- **Password:** `GithubRDP123!`
- **Session Duration:** 6 Hours (Auto-cycling)
- **Nodes:** 2 Parallel Instances (Alpha & Bravo)
- **Hostnames:** `RDP2-Alpha-X` and `RDP2-Bravo-X`

## 🛠️ Loop Management

### 🛑 How to Stop the Loop
To break the 24/7 cycle, create a file in this repository named exactly:
- `STOP` — This prevents the Trigger job from starting the next 6-hour session.

### 🔄 How to Restart
1. Delete the `STOP` file from the repository.
2. Go to the **Actions** tab.
3. Select the **RDP2-247** workflow.
4. Click **Run workflow**.

## 🛡️ Repository Secrets
For this repository to function, you **must** add these secrets in **Settings > Secrets and variables > Actions**:

| Secret | Value |
| :--- | :--- |
| `TS_AUTHKEY` | Your Tailscale Auth Key (**Must be REUSABLE**) |
| `TELEGRAM_TOKEN` | Your Telegram Bot API Token |
| `TELEGRAM_TO` | Your Telegram Chat/User ID |

## 🧹 Automated Cleanup
This repository features a **Delayed Force-Wipe** system. 
- Every 6 hours, the `Trigger` job waits 45 seconds for the GitHub API to sync.
- It then automatically deletes its own history to keep the Actions dashboard clean.

## ⚠️ Troubleshooting
- **Only one machine shows in Tailscale?** Verify that your `TS_AUTHKEY` is set to "Reusable" in the Tailscale admin console.
- **Workflow not deleting?** Ensure you have enabled **Read and write permissions** and checked the box for **"Allow GitHub Actions to create and approve pull requests"** in the Actions General settings.
- **Critical Alerts:** If you receive a Telegram alert saying "FAILED PREMATURELY,"
