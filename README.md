# LLVM IronArc Backend

This repository contains a copy of the LLVM compiler project, with an added backend to generate assembly and machine code targeting the IronArc platform. This repository is based on **LLVM 6.0.1**.

## Why?
	* LLVM is a compiler infrastructure project. Code in languages such as C, C++, Rust, etc., are loaded into a "frontend", where they are transformed into a common IR format. This format is then given to a backend that produces assembler or machine code for a given platform, such as x86 or ARM.
	* Front-ends and back-ends are interchangeable and modular, so C++ can be compiled to ARM, Rust can be compiled to Lanai, etc.
	* LLVM is extensible; new frontends can be created for languages, and new backends can be created for target platforms. Any such backend now supports every LLVM frontend language.
	* Creating an IronArc backend allows every LLVM language to be compiled to an IronArc executable. This opens up the possibilities for writing high-level IronArc applications.
	
## Goals:
	* To create an LLVM backend that is able to produce valid IronArc assembly code from any frontend language.
	* We do not care about making LLVM compile down to IronArc executable code. Printing assembly alone is fine, it's easier to check and IronAssembler can handle it.
		* although we may need to do straight executable, too. Unless I want to make InstrInfo emit UTF-8 strings...
	* Optimizations are nice, but not the main focus right now. If we get them, great, but we won't go out of our way to add them right now. The first thing is to just get it running at all.
	* Most of this will be done by porting existing backends for simpler platforms, such as Lanai or Cpu0 (see link below)
	
## Links:
	* Creating an LLVM Backend for the Cpu0 Architecture: https://jonathan2251.github.io/lbd/
	* Adventures with LLVM: http://www.cs.utah.edu/~sjosef/useful_stuff/llvm_log.html
		* LLVM with Trax Installation: http://www.cs.utah.edu/~sjosef/useful_stuff/llvm_trax_install.html
	* LLVM on Visual Studio: https://llvm.org/docs/GettingStartedVS.html
	