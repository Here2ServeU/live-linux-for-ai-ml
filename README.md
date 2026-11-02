# Linux for AI-ML Systems · Free Live Sessions

Find the model, feed it safely, keep it running: Linux the way AI engineers use it.

Free, live, 30-minute sessions with **Dr. Emmanuel Naweji** ([Transformed 2 Succeed](https://transformed2succeed.com)).
This course is presented on **Week 1, Monday at 7:30 PM Central** of a 4-week rotation (8 courses, every Monday and Thursday).
This repo holds the slides, the recording of every live session, and the notes and links from each one.

## Session recordings

| Date | Recording | Notes |
|---|---|---|
| _First session coming soon_ | | |
<!-- sessions:end -->

## What the session covers

1. **The Machine Under Your Model**: File at rest, process at work. Diagnose a server you've never seen.
2. **Feed the Model**: Space · Owner · Secret: the pre-flight that saves your GPU hours.
3. **Keep It Running**: Don't guess. Grep. Catch a silent out-of-memory kill and fix it.

## Three things to remember

- **File at rest. Process at work.**: Module 1. First question on any broken server: which one is it?
- **Space · Owner · Secret**: Module 2. The pre-flight before any long job or download.
- **Don't guess. Grep.**: Module 3. Read the logs, in order, before you restart.

## Try it yourself

Clone the course lab repo: [linux-for-ai-ml](https://github.com/Here2ServeU/linux-for-ai-ml)

**Module 1 · The Machine Under Your Model**: Small tools, joined by pipes

```bash
du -sh * | sort -h
du -ah models | sort -rh | head -5
```
**Module 2 · Feed the Model**: Lock the secret, load the key

```bash
chmod 640 data/tickets.jsonl
ls -l .env && chmod 600 .env
source .env && echo ${LAB_HF_TOKEN:0:6}
```
**Module 3 · Keep It Running**: Lab: climb the ladder after the kill

```bash
pgrep -af serve.py || echo 'not running'
tail -3 logs/server.log
grep -i 'killed process' logs/*.log
```

## Slides

[`slides/01_Linux_for_AI_ML_Systems_Free_Live_Session.pptx`](slides/01_Linux_for_AI_ML_Systems_Free_Live_Session.pptx): the presenter deck, with full speaker notes.

## Free live session schedule (Mondays and Thursdays, 7:30 PM Central)

| Week | Day | Course |
|---|---|---|
| Week 1 | Monday | **Linux for AI-ML Systems** (this repo) |
| Week 1 | Thursday | [Python for AI-ML](https://github.com/Here2ServeU/live-python-for-ai-ml) |
| Week 2 | Monday | [Zero to AI-ML Systems Engineering](https://github.com/Here2ServeU/live-zero-to-ai-ml) |
| Week 2 | Thursday | [DevOps for AI-ML Systems](https://github.com/Here2ServeU/live-devops-for-ai-ml) |
| Week 3 | Monday | [SRE for AI-ML Systems](https://github.com/Here2ServeU/live-sre-for-ai-ml) |
| Week 3 | Thursday | [GPU Optimization for AI-ML Systems](https://github.com/Here2ServeU/live-gpu-optimization-for-ai-ml) |
| Week 4 | Monday | [FinOps for AI-ML Systems](https://github.com/Here2ServeU/live-finops-for-ai-ml) |
| Week 4 | Thursday | [AI Agent Operations](https://github.com/Here2ServeU/live-ai-agent-operations) |

## Want all of it?

The membership gives you **all 8 courses, every module and every lab, for $49/month**, plus a live session every month where we build something together.
Join at **https://transformed2succeed.com**.

---

### For the presenter: logging a session

After each live session, run:

```bash
bash scripts/new-session.sh 2026-11-03 "https://link-to-the-recording"
git add -A && git commit -m "Session 2026-11-03" && git push
```

This creates `sessions/2026-11-03.md` from the template (fill in the Q&A and links) and adds a row to the recordings table above.
