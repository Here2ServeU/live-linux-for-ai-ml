# Linux for AI-ML Systems · Free Live Sessions

Find the model, feed it safely, keep it running: Linux the way AI engineers use it.

**Free · Live · 30 minutes · Mondays and Thursdays, 7:30 PM Central** · with Emmanuel N. ([Transformed 2 Succeed](https://transformed2succeed.com))

### [Register free on Zoom](https://us06web.zoom.us/meeting/register/fT235rLjQaihJYrWj2_vjw)

Register once and you're in for every session. Zoom emails you the join link and reminders. Bring your questions: every session ends with live Q&A.

## Watch the recordings

Missed a session or want to watch it again? Recordings are added here after each live session.

| Date | Recording |
|---|---|
| _Coming after the first session_ | |

## Download the slides

**[01_Linux_for_AI_ML_Systems_Free_Live_Session.pdf](slides/01_Linux_for_AI_ML_Systems_Free_Live_Session.pdf)** (PDF)

## What you'll learn

1. **The Machine Under Your Model**: File at rest, process at work. Diagnose a server you've never seen.
2. **Feed the Model**: Space · Owner · Secret: the pre-flight that saves your GPU hours.
3. **Keep It Running**: Don't guess. Grep. Catch a silent out-of-memory kill and fix it.

## Three things to remember

- **File at rest. Process at work.**: Module 1. First question on any broken server: which one is it?
- **Space · Owner · Secret**: Module 2. The pre-flight before any long job or download.
- **Don't guess. Grep.**: Module 3. Read the logs, in order, before you restart.

## Try it yourself

Get the hands-on labs here: [linux-for-ai-ml](https://github.com/Here2ServeU/linux-for-ai-ml)

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

## All free live sessions

A different course every session. The rotation repeats every 4 weeks, so if you miss one, it comes back around.

| Week | Day | Course |
|---|---|---|
| Week 1 | Monday | **Linux for AI-ML Systems** (you are here) |
| Week 1 | Thursday | [Python for AI-ML](https://github.com/Here2ServeU/live-python-for-ai-ml) |
| Week 2 | Monday | [Zero to AI-ML Systems Engineering](https://github.com/Here2ServeU/live-zero-to-ai-ml) |
| Week 2 | Thursday | [DevOps for AI-ML Systems](https://github.com/Here2ServeU/live-devops-for-ai-ml) |
| Week 3 | Monday | [SRE for AI-ML Systems](https://github.com/Here2ServeU/live-sre-for-ai-ml) |
| Week 3 | Thursday | [GPU Optimization for AI-ML Systems](https://github.com/Here2ServeU/live-gpu-optimization-for-ai-ml) |
| Week 4 | Monday | [FinOps for AI-ML Systems](https://github.com/Here2ServeU/live-finops-for-ai-ml) |
| Week 4 | Thursday | [AI Agent Operations](https://github.com/Here2ServeU/live-ai-agent-operations) |

## Want the full course?

The membership gives you **all 8 courses, every module and every lab, for $49/month**, plus a live session every month where we build something together.

**[Join at transformed2succeed.com](https://transformed2succeed.com)**
