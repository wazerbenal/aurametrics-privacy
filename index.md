# AuraMetrics Privacy Policy


**Effective date:** 1 December 2026

AuraMetrics collects no personal data for us. We, Wazer Benal ("we", "us"), do not run any server that AuraMetrics talks to, and the app contains no analytics, telemetry, advertising or crash reporting that sends data to us.

AuraMetrics is a hardware monitor for Windows. It reads information from your own PC and stores it on your own PC. Data leaves your PC in only two cases, and only when you start them yourself:

1. **AI analysis**, when you have turned it on, entered your own API key and clicked Analyze on an alert. Redacted diagnostic evidence goes to the AI provider you chose.
2. **Crash dump analysis**, when you click Analyze on a dump. The Windows debugger downloads debug symbols from Microsoft, which tells Microsoft the names and versions of the program modules in that dump.

AuraMetrics is sold through Steam. Valve's own privacy policy covers what Steam collects about your purchase and play time; this policy covers only the AuraMetrics app.

## What AuraMetrics reads on your PC

AuraMetrics runs with administrator rights because several sensors and Windows logs can only be read that way. It uses those rights to read, never to change, the following:

| Source | What is read | Why |
| --- | --- | --- |
| Hardware sensors | CPU, GPU, memory, fan, pump and coolant readings, through LibreHardwareMonitor and the separately installed PawnIO driver | Dashboard panels and alerts |
| Windows event logs | Hardware errors, driver resets, device failures, shutdowns, power events, blue screens, app crashes and hangs | Alerts and incident evidence |
| Crash reports and dumps | Windows Error Reporting reports, blue screen and live kernel dumps, app dumps | The Dumps scan and, when you ask, debugger analysis |
| Running processes | Name, ID, status, user account, CPU and memory use, architecture and description, from system-wide queries | The Processes page and crash alerts for watched apps |
| System details | CPU, memory modules, GPUs and drivers, motherboard and BIOS, Windows version, disks, and installed-program entries used to find the chipset driver | System Info page and driver change tracking |

AuraMetrics never opens another process, reads or writes another program's memory, injects code, hooks input or installs a kernel driver of its own. It never changes or deletes event logs, crash reports or dump files.

### What AuraMetrics stores

Everything AuraMetrics writes stays in `%LOCALAPPDATA%\AuraMetrics` on your PC. You can open that folder from the Help page and delete any of it at any time.

| File | Contents | How long it is kept |
| --- | --- | --- |
| `alerts.log`, `alerts.old.log` | Every alert raised | Until the log reaches 5 MB, then one older file is kept |
| `sensor-history.jsonl` and `.old` | The last minute of sensor readings | Overwritten continuously |
| `sensor-snapshots\` | Sensor readings around Critical alerts and app crashes | The newest 50 |
| `sensor-diagnostics.log` | Detected hardware and environment | Rewritten at each launch |
| `driver-history.json` | Driver version changes | Until you delete it |
| Settings files (`*.json`) | Your layout, alert limits, watched processes and AI settings | Until you delete them |
| `ai-key-*.bin` | Your AI API keys, encrypted with Windows DPAPI for your Windows account | Until you remove the key or the file |
| `symbols\` | Debug symbols downloaded for dump analysis | Up to the size limit you set (1 GB by default) |

Uninstalling AuraMetrics through Steam leaves this folder in place. To remove all AuraMetrics data, delete the `%LOCALAPPDATA%\AuraMetrics` folder after uninstalling.

## Optional AI analysis

AI analysis is off by default and sends nothing until you turn it on in Settings, choose a provider, enter your own API key and click Analyze with AI on an alert. Before anything is sent, AuraMetrics shows you exactly what will be sent and where it will go, and you can cancel.

**What is sent.** For the alert you chose: the alert itself, related Windows event log entries, a summary of the sensor readings around it, your hardware, firmware, Windows and driver details, recent driver version changes, and the debugger's crash dump result if you ran one. The dump file itself is never sent.

**What is removed first.** Before sending, AuraMetrics replaces your Windows user name and profile paths, computer and domain names, account SIDs, network share host names, email addresses, IP and MAC addresses, serial numbers, product keys and device instance IDs with placeholders. Redaction is automatic and pattern-based, so it may not catch every piece of identifying text, which is why you see the payload before it goes.

**One exception.** If the provider address is a server running on your own PC (localhost, such as Ollama or LM Studio) and you tick "Send evidence to this local server without removing names and serial numbers", the evidence is sent unredacted to that local server only. Any server elsewhere, including another PC on your network, always gets redacted data.

**Who receives it.** The provider you pick: OpenAI, Anthropic, Google Gemini, xAI, Mistral, DeepSeek, OpenRouter, Groq, a local Ollama or LM Studio, or any compatible address you enter. You have your own account with that provider, and its privacy policy and terms govern what it does with the data, including whether it keeps it or uses it for training. We never see the data or your key.

**Your API keys.** Each key is stored encrypted with Windows DPAPI so only your Windows account on this PC can read it, and it is sent only to the provider it was entered for.

## Crash dump analysis

When you click Analyze on a crash dump, AuraMetrics runs Microsoft's Windows debugger (WinDbg's cdb), which you install yourself. The debugger downloads debug symbols from Microsoft's public symbol server, which reveals the names and versions of the program modules in the dump to Microsoft. The dump itself stays on your PC. AuraMetrics tells you this before you run it. Microsoft's privacy statement covers that request.

## Third-party components

AuraMetrics reads sensors through LibreHardwareMonitor and the PawnIO driver, which you install separately from pawnio.eu. Neither sends data to us. PawnIO, WinDbg and your AI provider are separate products with their own terms.

## Your choices and rights

Because we hold no data about you, there is nothing for us to access, correct, export or delete on request. You control everything AuraMetrics stores: delete files in `%LOCALAPPDATA%\AuraMetrics`, remove an API key in Settings, or turn AI analysis off. For data you sent to an AI provider, contact that provider. If you live in the EU, UK, California or another region with privacy laws, those rights apply to anyone who holds your data, and for AuraMetrics that is you and the provider you chose.

## Children

AuraMetrics collects no personal data from anyone, including children.

## Changes to this policy

If a future version changes what AuraMetrics reads, stores or sends, we will update this policy, change the effective date and note the change in the Steam patch notes before that version ships.

## Contact

Wazer Benal

wazer.benal@gmail.com
