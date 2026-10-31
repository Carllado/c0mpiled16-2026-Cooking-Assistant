# Cooking Assistant — UCSD c0mpiled-16 Hackathon 2026

**Embedded hardware, camera streaming, and prototype integration | ESP32-CAM · ESP32-S3-BOX-3 · RPLIDAR**

> **About this repository:** This is my personal engineering case study of a collaborative hackathon project. It documents the hardware I tested, what the team demonstrated, the challenges we encountered, and possible next steps. It is **not** a copy of the team's source-code repository or a claim of sole authorship.
>
> **Original team repository:** [joshuammerced/compile16Hackathon](https://github.com/joshuammerced/compile16Hackathon)

## 1. Project overview

Cooking Assistant was a hackathon concept for a camera- and voice-assisted cooking companion. We wanted to explore how an embedded system could observe a cooking environment, offer context-aware guidance, and eventually help people notice potentially unsafe situations around a stove or hot cookware.

Our proposed application combined a camera feed, perception of relevant objects and human activity, a voice interface, and a web-based user experience. **The hackathon outcome was an early prototype, not a validated or fully autonomous cooking-safety system.**

## 2. Problem and proposed solution

Cooking often divides attention between food preparation, heat sources, utensils, and other tasks. Our question was: *Could a low-cost, embedded assistant make cooking status easier to monitor and interact with?*

We explored a system that could eventually:

1. Observe a cooking area through an ESP32-CAM.
2. Interpret the scene, including a person and cooking equipment, using computer vision.
3. Give visual status updates or contextual alerts through a web interface.
4. Allow hands-free questions or instructions through an ESP32-S3-BOX-3 voice interface.

These were **design goals**, not all capabilities completed during the hackathon. In particular, no reliable food-doneness, burn-risk, or temperature measurement was established.

## 3. System concept and actual testing

### Intended architecture

```text
ESP32-CAM
   |
   | Wi-Fi video stream
   v
Computer / vision processing (planned scene understanding)
   |
   v
Backend / cooking-state logic (planned integration)
   |
   +----------------------> Web interface / guidance
   |
   +----------------------> Context for voice assistant (planned)
                                  ^
                                  |
                         ESP32-S3-BOX-3
                         microphone / speaker

Optional exploration: RPLIDAR for environmental sensing
(not integrated into the cooking-assistant pipeline)
```

### What we tested during the hackathon

- **ESP32-CAM:** Successfully streamed video to a web-based viewing setup.
- **ESP32-S3-BOX-3:** Investigated device setup and voice integration, but did **not** complete a functioning voice interaction pipeline for the final demonstration.
- **RPLIDAR:** Tested the sensor separately as an exploration of environmental sensing; it was **not** part of the completed cooking-assistant system.
- **Web demonstration:** Presented a **simulated prototype** to communicate the intended user experience; it should not be confused with a fully integrated live perception and alert system.

## 4. My personal contributions

My primary focus was **hardware setup, device testing, and integration troubleshooting**.

### ESP32-CAM — video streaming

- Worked on setting up the ESP32-CAM for wireless video capture.
- Tested the camera feed and confirmed that video could be accessed through the web-based setup.
- Explored how the feed could later support recognition of people and cooking equipment.

**Outcome:** Camera streaming worked. A complete, validated cooking-scene understanding pipeline was **not** demonstrated.

### ESP32-S3-BOX-3 — voice-interface experiments

- Worked on troubleshooting the ESP32-S3-BOX-3 as a possible hands-free input/output device.
- Encountered device setup and display/integration problems, including the **“Home Assistant not found”** issue during experimentation.
- Investigated the gap between having voice-capable hardware and getting a dependable interaction with the rest of the application.

**Outcome:** The BOX-3 was **not** fully integrated into the final hackathon demonstration.

### RPLIDAR — exploratory sensor testing

- Conducted separate tests of the available RPLIDAR hardware.
- Considered whether spatial sensing might be helpful for the broader product concept.

**Outcome:** Exploratory sensor testing only; **no working LiDAR-to-cooking-assistant integration** was completed.

### Hardware/software coordination

- Helped identify hardware constraints and integration gaps during rapid prototyping.
- Collaborated with teammates working on the software concept, interface, and presentation.
- Supported the team in distinguishing a live hardware result from functionality shown through simulation.

## 5. Hackathon results

| Component or feature | Result at the hackathon | Notes |
| --- | --- | --- |
| ESP32-CAM video streaming | **Working** | Camera feed accessible through the test setup |
| Web concept demonstration | **Demonstrated as a simulation** | Communicated intended product behavior |
| ESP32-S3-BOX-3 voice interaction | **Not fully integrated** | Device setup/integration remained unresolved |
| RPLIDAR experiment | **Tested separately** | Not connected to the end-to-end application |
| Automated person/pot perception | **Not verified as a completed feature** | Part of the proposed design |
| Real-time safety alerts | **Not verified as a completed feature** | Requires additional sensing, logic, and validation |
| Fully integrated cooking-assistant system | **Not completed** | Hardware and software components remained partially separate |

**Validation note:** We did not establish formal measurements of detection accuracy, latency, false-alarm rates, or safety performance. The prototype should not be represented as a dependable safety-critical device.

## 6. Engineering challenges and lessons learned

### A. Integration takes longer than isolated component tests

A camera streaming successfully does not automatically mean its output is connected to a perception model, backend state, and a usable interface. Next time I would define and test the input/output contract between each subsystem earlier.

### B. Voice-enabled hardware still needs a reliable software path

The ESP32-S3-BOX-3 posed configuration and communication challenges. A better plan is to confirm a minimal microphone-to-response demonstration before attempting to integrate it with an entire application.

### C. Hardware experiments need clear power and connectivity plans

Microcontrollers and sensors differ in power requirements, device configuration, and communication interfaces. Future prototypes should document the power source, connection diagram, expected current draw, network setup, and repeatable test procedure.

### D. Simulated demos are useful but must be labeled clearly

A simulation helped communicate the concept despite incomplete integration. I learned to report **what was measured**, **what was demonstrated independently**, and **what was only proposed** as separate categories.

## 7. What I would build next

If I continue developing the project, I would prioritize milestones with measurable acceptance criteria:

1. **Repeatable camera test:** Record stream startup time, stability, and approximate latency across multiple trials.
2. **Basic perception experiment:** Collect a small labeled dataset and test detection of a person and cooking equipment; report false detections and missed detections.
3. **Standalone voice demonstration:** Get one voice command into the BOX-3 and deliver an audible response with recorded test evidence.
4. **Minimum end-to-end integration:** Connect one real detected event to a visible interface update; avoid adding multiple new features at once.
5. **Reliability and safety review:** Test connectivity loss, sensor uncertainty, false alerts, privacy considerations, and recovery behavior before making any safety claims.

## 8. Team collaboration and credits

This was a **collaborative UCSD c0mpiled-16 hackathon project**. My emphasis was hardware experimentation and integration testing; teammates contributed software development, research, presentation, and other project work.

**Team source code and shared implementation:** [joshuammerced/compile16Hackathon](https://github.com/joshuammerced/compile16Hackathon)

The team repository contains folders for hardware, voice, backend, and LLM experiments. Please refer to it for the shared source code. This personal repository is focused on my engineering documentation; it should not be treated as a runnable copy of the team application.

## 9. Evidence to add

To make the project easier to evaluate, I plan to add any evidence I can verify and have permission to publish:

- Photos of the actual hardware setup and connections.
- A screenshot or short video showing ESP32-CAM streaming.
- Notes or logs from BOX-3 troubleshooting.
- A short clip or screenshots of the simulated final demonstration, clearly labeled **simulation**.
- Reproducible sensor test notes or code that I personally authored.

---

*Event: UCSD c0mpiled-16 Hackathon 2026 · Focus: embedded systems, prototyping, and hardware/software integration.*
