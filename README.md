# keepalive

Keeps free-tier backends awake by pinging them every 5 minutes with a scheduled
GitHub Actions workflow ([`keep-alive.yml`](.github/workflows/keep-alive.yml)).

| Service | Host | Pinged URL |
|---|---|---|
| ExamSense backend | Render (sleeps after 15 min idle) | https://examsense-vlv9.onrender.com/ |
| AI Pen Tester | Hugging Face Spaces (sleeps after 48 h idle) | https://hkfdihjebfvhdfbvgre-ai-pentester.hf.space/health |

To add a service, add a `name url` line to the list in the workflow.

A failed ping shows up as a warning on the run, not a failure, so an outage
doesn't send an email every 5 minutes. A monthly heartbeat commit keeps GitHub
from disabling the schedule after 60 days without activity.
