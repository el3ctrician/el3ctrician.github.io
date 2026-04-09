+++
draft = false
title = 'What 10 years of digital design has taught me'
showReadingTime = true
showDate = true
showTableOfContents = true
showSummary = true
summary = "A reflection from the field after 10 years of digital design"
date = 2026-04-09
showAuthor = true
showPagination = true
showComments= true
+++

# My personal lessons from 10 years between FPGAs and ASICs

*opinionated but grounded*

---

I’ve been fortunate to work on systems now in production — from ASICs in biomedical devices, to FPGAs in computer vision, to control logic for particle physics infrastructure. Designing digital systems that work outside of a simulation is hard. Getting them to production — reliably, efficiently, and without late-stage surprises — is even harder.

After 10 years working across FPGA and ASIC platforms, I’ve come to believe that most digital design projects don’t fail from bad code. They fail from bad assumptions, skipped verification, and workflows that fight the tools instead of leveraging them.

These aren’t textbook rules. They’re patterns I’ve seen work (or fail) across multiple tape-outs and lab bring-ups. In this post, I want to highlight some hard-earned lessons and the kinds of technical interventions that have made a measurable difference in real systems.

---

## Tools and language constructs are here to help!

It is no secret that a lot of people in the industry are, understandably, afraid of the synthesizer. Language standard is one thing while the tools support for it is often very slow or out of the box not present. This leads to a tendency to not trust the synthesizer of being smart enough and avoid using higher level abstraction.

Some teams, particularly in legacy VHDL environments, default to ultra-granular RTL out of habit. While control feels predictable, it often fights the synthesizer instead of leveraging it.

I quickly learned that the best way is to "study" your synthesizer slowly by observing the resulted logic to understand how the tool works and use it for your benefit. You can then use moderate description and let the synthesizer figure it out for you slowly getting to know your tool.

Clean RTL is not about clever tricks. It’s about expressing intent so the tools can optimize for you — not in spite of you.

---

## Verification: Not Optional, Even in FPGA

There’s a common belief that in FPGA you can "just test it on the board." That mindset causes more delays and design bugs than almost anything else.

Debugging a poorly verified design in a lab is slow, incomplete, and blind compared to testbench-driven workflows. Think about the time you need to re-synthesize every time you want to see a new signal in the debug or even worse deciding which is the root cause to observe in the first place.

It is clear that the need of good verification environment is crucial for FPGAs and for ASIC, with different scope and roles. Typically in an FPGA flow you want to architect a verification environment that also serves to reproduce observed bugs in the lab so you can have full access to everything happening in the system inside the simulator. While in ASIC the focus is more on covering as many cases as needed to ensure that your HDL will be taped out correctly and avoiding re-masking.

That said, not all teams can afford full UVM or in-depth test environments. And thanks to a lot of great tools out there you can create a powerful environment with minimal investment. I’ve helped teams bridge that gap by integrating Python-based golden models, through DPI, directly into SystemVerilog testbenches — enabling functional checks without rewriting complex algorithms.

---

## Real Interfaces, Real Challenges

High-speed interfaces are where theory and reality often diverge. Over the years, I’ve built:

- A **SLVS-EC Transmitter**, fully parameterized and portable
- A **Dynamic Phase Alignment system** to capture high-resolution Sony image sensor data using standard I/Os — avoiding costly transceivers
- An **interface and control logic layer for a particle accelerator (CNAO)**, integrating deeply with legacy systems and complex timing constraints

Each of these required a deep understanding of signal integrity, latency tolerance, clock domain crossing, and — often more importantly — how to squeeze performance from devices that weren't originally designed for such use cases. Designing such interfaces requires a lot of practical solutions and a process of choosing between bad and worse to balance your trade-off. While it is always tempting to write a clean and understandable HDL sometimes you have to accept the fact that you need some tricks to work around protocols quirks and target limitation.

When it comes to interfaces, I would say that Dynamic phase alignment shines on FPGAs, whereas ASIC flows demand rigorous timing constraints from day one.

---

## Transitioning from FPGA to ASIC: Do It Early, or Regret It Later

If you plan on testing on FPGA to later transition to ASIC, never build systems around vendor IPs that can’t be retargeted. Harden your timing constraints and most importantly remember that on FPGAs, logic is mapped to LUTs, so complexity doesn’t always correlate linearly with area. On ASICs, however, gate count, wire length, and memory hierarchy directly impact area and timing, making early architectural planning critical.

Also FPGAs lean heavily on distributed memories and shift registers, which synthesize almost transparently. In ASIC, however, every inferred memory must be explicitly planned for area, timing, and physical placement. Treat memory architecture as a first-class design constraint from day one.

My personal flow includes:
1. **Removing vendor-specific logic early**
2. **Abstracting IO and memory interfaces**
3. **Running trial synthesis and P&R**

Always make sure that you have an eye of your ASIC backend issues and that they are addressed before even targeting ASIC.

---

## Automation Isn’t Optional

If you’re still generating your regmap by hand or if you are using ancient methods to hold crucial design data to be copied manually by a designer, you are willingly opening the door for errors in your flow. For one client I replaced an entire RTL generation workflow using Python, by recovering the data through text files and excel sheet parsing. No more dedicated person taking input from other teams and manually converting them to HDL. The result: maintenance time, i.e., time between specification updates and HDL implementation, cut by over 80%, less bugs and errors due to generated code and making continuous integration trivial.


---

## Conclusion: It's Not Just What You Build, But How You Think

Whether I’m reviewing architecture, optimizing RTL, or pushing designs through place-and-route, I care deeply about one thing: **robust systems built with clarity and intent**.

I believe in:
- Writing code that’s portable by default
- Using automation to reduce human error
- Leveraging toolchains *completely*, not fearfully
- Calling out flawed assumptions early — even when it’s uncomfortable

What lessons have you learned during your journey? I’d love to compare notes in the comments.

*Image by <a href="https://pixabay.com/users/compileideas-6085846/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4972649">Amol Sharma</a> from <a href="https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4972649">Pixabay</a>*