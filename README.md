<div align="center">

<img src="https://avatars.githubusercontent.com/zizhengwang2026" alt="avatar" width="132" style="border-radius:50%;border:3px solid #6366F1;box-shadow:0 4px 16px rgba(99,102,241,0.35)"/>

# <span style="color:#6366F1;">Zizheng Wang</span>&nbsp;👋

### MSc Candidate · Mechanical Engineering · Zhejiang University

<p>
  <img src="https://komarev.com/ghpvc/?username=zizhengwang2026&label=Profile%20Views&color=6366F1&style=flat-square" alt="views"/>
</p>

> 🚀 *"I turn soft matter into learning machines — where mechanics meets intelligence."*

</div>

---

<p align="center">
  <a href="#-about-me">About</a> &nbsp;·&nbsp;
  <a href="#-research-focus">Research</a> &nbsp;·&nbsp;
  <a href="#-featured-builds">Projects</a> &nbsp;·&nbsp;
  <a href="#-learning-log">Blog</a> &nbsp;·&nbsp;
  <a href="#-connect">Connect</a>
</p>

---

## 🧭 About Me

<div style="background:#F8FAFC;border-left:5px solid #6366F1;padding:14px 18px;border-radius:8px;">

- 🎓 **MSc Candidate**, Mechanical Engineering — Zhejiang University
- 🤖 Building the bridge between **physical machines** and **machine intelligence**
- 💡 Hands-on: teleoperation → **imitation learning (ACT)** deployed on a real **SO-101** arm
- 📍 Hangzhou, China

</div>

---

## 🌟 Research Focus

<div align="center">

<table>
  <tr>
    <td width="50%" align="center" style="background:#EEF2FF;border:1px solid #C7D2FE;border-radius:10px;padding:14px 10px;"><b>🤖 Embodied AI</b><br/><sub>learning on real bodies</sub></td>
    <td width="50%" align="center" style="background:#ECFEFF;border:1px solid #A5F3FC;border-radius:10px;padding:14px 10px;"><b>🧠 AI Agents</b><br/><sub>plan · reason · act</sub></td>
  </tr>
  <tr>
    <td width="50%" align="center" style="background:#F0FDF4;border:1px solid #BBF7D0;border-radius:10px;padding:14px 10px;"><b>🦾 Soft Robotics</b><br/><sub>compliant, morphologically smart</sub></td>
    <td width="50%" align="center" style="background:#FEFCE8;border:1px solid #FDE68A;border-radius:10px;padding:14px 10px;"><b>🦿 Humanoid Robots</b><br/><sub>full-body embodiment</sub></td>
  </tr>
  <tr>
    <td width="100%" align="center" style="background:#FFF1F2;border:1px solid #FECDD3;border-radius:10px;padding:14px 10px;" colspan="2"><b>⌚ Wearable Devices</b><br/><sub>soft exo-suits · rehab · skin-like sensing</sub></td>
  </tr>
</table>

</div>

---

## 🛠️ Tech Stack

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54"/>
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/>
  <img alt="LeRobot" src="https://img.shields.io/badge/LeRobot-FFD21E?style=for-the-badge&logoColor=black"/>
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
  <img alt="Git" src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img alt="Linux" src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"/>
</p>

<div style="background:#F8FAFC;border-left:5px solid #06B6D4;padding:12px 16px;border-radius:8px;">

**📈 Leveling up (in progress):**

| Skill | Progress |
|---|---|
| C++ | <div style="background:#E2E8F0;border-radius:999px;height:9px;width:100%;"><div style="background:#6366F1;height:9px;border-radius:999px;width:40%;"></div></div> |
| ROS 2 | <div style="background:#E2E8F0;border-radius:999px;height:9px;width:100%;"><div style="background:#06B6D4;height:9px;border-radius:999px;width:30%;"></div></div> |
| Sim-to-Real (soft) | <div style="background:#E2E8F0;border-radius:999px;height:9px;width:100%;"><div style="background:#22C55E;height:9px;border-radius:999px;width:35%;"></div></div> |
| RL fine-tuning | <div style="background:#E2E8F0;border-radius:999px;height:9px;width:100%;"><div style="background:#F59E0B;height:9px;border-radius:999px;width:50%;"></div></div> |

</div>

---

## 🚀 Featured Builds

### 🦾 SO-101 × ACT — Real-Hardware Imitation Learning
> A full **collect → train → deploy** embodied-AI pipeline I built hands-on. No simulation shortcut — every step ran on real hardware.

**Stack:** D-Robotics S600 (RDK edge-AI board) · SO-101 6-DOF arm · HuggingFace **LeRobot** · **ACT**

**What I did, end-to-end:**
1. 🔧 Flashed the S600 with XBurn; SSH in; built a Miniconda (aarch64) env + installed LeRobot
2. 📐 Calibrated **leader & follower** arms with FEETECH (ID / limits / center)
3. 🎮 **Teleoperated** to collect a demonstration dataset (dual camera + 6 joint angles)
4. 🧠 Trained an **ACT** policy — *action chunking + CVAE + Transformer*
5. 🤖 Deployed **policy-server + ACT-client** → the arm grasps autonomously from vision

**Hard parts I solved myself:** SSH drop during flash · conda arch mismatch (x86 vs aarch64) · Debian `externally-managed-environment` pip block · servo sync · ACT train/inference.

**Result:** the arm completes vision-based grasps on its own — my first real **perceive → decide → act** embodied loop.

```bash
# the 8-step pipeline I actually ran
1_calibrate_follower.sh   # calibrate follower arm
2_replay_episode.sh       # audit collected data
train                     # train the ACT policy
check                     # inspect training loss
3_start_policy_server     # load the trained model
4_run_act_client          # drive the arm in real time
```

🔗 Code & notes → [`embodied-dea-journey/so101-act`](https://github.com/zizhengwang2026/embodied-dea-journey)

---

### 🌱 [embodied-dea-journey](https://github.com/zizhengwang2026/embodied-dea-journey)
Zero → one learning track: **Embodied AI (IL / VLA) × soft robotics**.
Demos, notes, weekly logs. *The repo HR actually reads.*

### 📚 [dea-soft-robotics-papers](https://github.com/zizhengwang2026/dea-soft-robotics-papers)
Curated reading notes on **soft robotics + learning control**.
Each paper → 3 questions / engineering meaning / how I'd use it.

### 🤖 [lerobot-dea-finetune](https://github.com/zizhengwang2026/lerobot-dea-finetune) *(planned)*
Bridging the LeRobot IL framework to soft-robot hardware: sensing → policy → motion.

---

## 📓 Learning Log

<!-- BLOG-POST-LIST:START -->
<!-- paste your latest article links here, one per week -->
<!-- BLOG-POST-LIST:END -->

> 🔗 Full blog: [CSDN](https://blog.csdn.net/ZizhengWang2023) · Series *"Embodied Self-Study Weekly #N"*

---

<details>
  <summary>💬 Tap to cheer me on</summary>
  <br/>
  <div align="center">
    <p><i>"Soft bodies, smart minds — keep building."</i> 🔥</p>
    <p>Thanks for visiting! Drop a ⭐ on a repo if something helped you.</p>
  </div>
</details>

---

## 🤝 Connect

<p>
  <a href="https://github.com/zizhengwang2026" style="display:inline-block;padding:8px 16px;margin:4px;border-radius:8px;background:#181717;color:#fff;text-decoration:none;font-weight:bold;">GitHub</a>
  <a href="mailto:williamshine2024@163.com" style="display:inline-block;padding:8px 16px;margin:4px;border-radius:8px;background:#EA4335;color:#fff;text-decoration:none;font-weight:bold;">Email</a>
  <a href="https://blog.csdn.net/ZizhengWang2023" style="display:inline-block;padding:8px 16px;margin:4px;border-radius:8px;background:#F5533D;color:#fff;text-decoration:none;font-weight:bold;">CSDN</a>
</p>

> 📍 Hangzhou · Zhejiang University

---

<sub>🪐 Built with curiosity. Last updated 2026-08-14 — v2 (young & clean).</sub>
