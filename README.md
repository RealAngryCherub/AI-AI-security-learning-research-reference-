# AI-AI-security-learning-research-reference-
A personal tracking index used to study AI model behaviors, open-source agent tools (like Hermes), and basic defensive sandboxing methods. Part of an ongoing weekly learning routine to understand model robustness.
 
# AI Security & Testing Notes

This repository acts as my personal notepad to keep track of links, tools, and ideas as I continue to learn about AI security. 

While I am familiar with basic system administration and networking tools, I am relatively new to AI tool security specifically. I use this space to stay proactive by spending time each week reading documentation, testing open-source projects, and learning how these systems function.

## Context & Approach
I maintain a home network environment utilizing tools like pfSense, Proxmox, and Wazuh (for monitoring) to emulate an enterprise grade netwok setup. Alongside a few headless servers for automation and remote workloads. Currently, I am experimenting with integrating local open-weight models to help process information, as well as running separate headless environments for dedicated agent automation.

Because allowing an model to interact with local command lines or read unvetted configuration files (`SKILL.md` structures) introduces noticeable security risks, I treat these AI tools as isolated, untrusted assets. 

I view the prompt injection links and testing tools listed below as basic Quality Assurance (QA) stress tests. The goal is to observe common failure points in model logic so I can better understand how to write secure prompts and configure proper boundaries before letting an agent touch my broader network setups, as well as continue to expose myself to new topics and continue learning.

---

## Utilities & Resources Under Review

### 1. Testing & Examples
*Simple datasets and prompt collections used to understand how models handle boundaries.*
*   [GitHub Topic: Prompt Injection](https://github.com) - Reviewing public examples to see how text inputs can confuse an AI.
*   [f/prompts.chat](https://github.com) - A list of system prompts that helped me learn how basic behavior rules are written for a model.

### 2. Scanners & Safety Tools
*Projects aimed at checking configuration files for safety or stopping unauthorized commands.*
*   [NVIDIA / SkillSpector](https://github.com) - A tool that scans AI setup files for unusual dependencies or instructions before execution.
*   [pipelab-org / pipelock](https://github.com) - A project designed to act like an external firewall to block unsafe commands from running.

---

## Baseline Isolation Measures (Work in Progress)
As I work through the gaps in my AI knowledge, I am keeping these experiments strictly contained using my existing network rules:

1.  **Strict Network Segmentation:** Keeping all headless agent automation and testing setups completely isolated on their own dedicated VLANs and separate VPN tunnels.
2.  **Container Sandboxing:** Ensuring local model tests run inside isolated, unprivileged Docker or LXC containers so mistakes do not impact the underlying host systems.
3.  **No Hardcoded Secrets:** Forcing all AI tools and configuration folders to pull credentials from environment variables rather than storing raw API tokens in files.
4.  **Manual Script Verification:** Reviewing the raw Python or shell scripts accompanying any community module before letting the model interact with it.

*Note: This repository is an active, in progress, notebook for a weekly learning routine. It will likely change as I continue to improve my understanding,and thus adjust my configurations.*
