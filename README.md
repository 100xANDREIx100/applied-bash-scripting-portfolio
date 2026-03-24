# 💻 Applied Bash Scripting Portfolio
![Bash](https://img.shields.io/badge/Language-Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)
![Linux](https://img.shields.io/badge/Environment-Linux_VM-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Status](https://img.shields.io/badge/Status-In_Progress-blue?style=for-the-badge)

This repository documents my journey mastering Linux shell scripting and system administration, following the intensive 7-hour [The Complete Bash Scripting Course](https://youtu.be/Sx9zG7wa4FA) by Dave Eddie. 

**Side-Quest Update:** To complement my command-line skills, I have expanded this portfolio to include mastering the ubiquitous terminal text editor, `vim`. This progress is tracked following the comprehensive [Vim Tutorial for Beginners](https://youtu.be/RZ4p-saaQkc) course by freeCodeCamp.

Instead of passively watching, I am building this portfolio to track my hands-on progress, keeping a clean record of both theoretical concepts and practical automation scripts.

## 🛠️ My Learning Methodology
* **Handwritten Documentation:** I take detailed handwritten notes in Microsoft OneNote to maximize memory retention. These are exported as `.pdf` files so they render natively and beautifully directly in the GitHub browser.
* **Progressive Scripting:** All practical code is written, tested, and debugged inside a dedicated and secure Linux Virtual Machine (VM). 
* **Version Control:** I use Git to continuously sync my notes from Windows and push my tested code from the Linux VM terminal.

## 📂 Repository Structure
The repository is organized modularly by course sections. Each section contains its own dedicated folders for theory and practice:

* `📁 XX.Complete_chapter_name/`
  * `📁 notes/` - Handwritten OneNote exports (PDFs) covering the theoretical concepts for this specific section.
  * `📁 scripts/` - Executable Bash scripts built during the hands-on labs for this section.

## ⚙️ How to Run the Scripts
Once the `scripts/` directories are populated, you can run any of the Bash scripts locally on a Linux machine or WSL environment:
1. Navigate to the specific section's scripts folder: `cd Section_03_Scripting_Fundamentals/scripts`
2. Ensure the script has execution permissions: `chmod +x script_name.sh`
3. Execute it: `./script_name.sh`

## 🚀 Course Syllabus & Progress Tracker

**Section 01: The Terminal & File System**
- [x] 01-00 Terminal and Finder
- [x] 01-01 Basic File Manipulation
- [x] 01-02 Hidden Files
- [x] 01-03 Searching in Files
- [x] 01-04 Paging Files

**Section 02: Core Tooling & Concepts**
- [x] 02-00 Man Pages
- [x] 02-01 Programs and Commands
- [x] 02-02 Basic Variables
- [x] 02-03 vim Crash Course
- [x] 02-04 File Permissions

**Section 03: Scripting Fundamentals**
- [ ] 03-00 Finally Scripting
- [ ] 03-01 User Input
- [ ] 03-02 Functions
- [ ] 03-03 Conditionals
- [ ] 03-04 For Loops
- [ ] 03-05 Input / Output
- [ ] 03-06 Chapter 3 Recap

**Section 04: Advanced Data & Execution**
- [ ] 04-00 Case Statements
- [ ] 04-01 Indexed Arrays
- [ ] 04-02 Associative Arrays
- [ ] 04-03 IFS Variable
- [ ] 04-04 Command Substitution
- [ ] 04-05 Arithmetic Expression
- [ ] 04-06 Process Substitution
- [ ] 04-07 Chapter 4 Recap

**Section 05: Text Processing & Searching**
- [ ] 05-00 cut and tr
- [ ] 05-01 sed, awk, and grep
- [ ] 05-02 Find Command

**Section 06: Execution & Debugging**
- [ ] 06-00 Bash Arguments
- [ ] 06-01 Pipe Status
- [ ] 06-02 Timing Commands

**Section 07: Code Architecture**
- [ ] 07-00 Sourcing Code
- [ ] 07-01 Curlies vs. Parens
- [ ] 07-02 Return vs. Output
- [ ] 07-03 Chapter 7 Recap

**Section 08: Parameter Handling**
- [ ] 08-00 Parameter Expansion
- [ ] 08-01 Array Expansion

**Section 09: Globbing (Pattern Matching)**
- [ ] 09-00 Basic Globbing
- [ ] 09-01 Extended Globbing
- [ ] 09-02 Glob Shell Options

**Section 10: Brace Expansions**
- [ ] 10-00 Brace Expansion
- [ ] 10-01 Braces and Globbing
- [ ] 10-02 Numeric Brace Expansion

**Section 11: Formatting & Parsing Data**
- [ ] 11-00 Understanding printf
- [ ] 11-01 Date Formatting
- [ ] 11-02 Regular Expressions
- [ ] 11-03 Using mapfile

**Section 12: Advanced Conditionals & Strings**
- [ ] 12-00 Brackets vs. Test
- [ ] 12-01 Special Strings

**Section 13: Inter-Process Communication**
- [ ] 13-00 Trap Signals
- [ ] 13-01 Named Pipes

**Section 14: Terminal User Interfaces (TUI)**
- [ ] 14-00 Color Output
- [ ] 14-01 Cursor Commands
- [ ] 14-02 Is a TTY

**Section 15: Environment Customization**
- [ ] 15-00 PS1 Variable
- [ ] 15-01 Customizing Bash
- [ ] 15-02 Readline Shortcuts

**Section 16: Common Bash Pitfalls**
- [ ] 16-00 Pitfall: ls
- [ ] 16-01 Aliases with Arguments
- [ ] 16-02 Pitfall: String Length

**Section 17: Outro & Bonus**
- [ ] 17-00 Forkbomb
- [ ] Bonus Credits
- [ ] Bonus Debugging Session

**Bonus Track: Vim Mastery (freeCodeCamp Course)**
- [x] 01. Motivation & Power of Vim
- [x] 02. Installation & Configuration
- [x] 03. The Basics (Opening, Saving, Quitting)
- [x] 04. Navigation & Editing Fundamentals
- [x] 05. Intermediate Key Bindings & Jumps
- [ ] 06. Macros & Registers
- [ ] 07. Neovim & Plugin Management
- [ ] 08. Vim Bindings in IDEs (VS Code, PyCharm)

## 🧰 Tools & Environment
* **OS:** Kali Linux (Virtual Machine)
* **Shell:** GNU Bash
* **Editor/IDE:** vim (CLI) & VS Code
* **Notes:** Microsoft OneNote (exported to PDF)

---
*Built with dedication. Always learning and open to feedback!*