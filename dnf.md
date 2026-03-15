## Update
- To check for updates:
  
  `dnf check-update`
  
  or
  
  `dnf check-upgrade`
  ```
  [hungtx@linux ~]$ dnf check-upgrade 
  Last metadata expiration check: 0:09:54 ago on Sun 20 Apr 2025 10:08:54 AM CEST.
  
  bpftool.x86_64                                                                    7.4.0-503.35.1.el9_5                                                         baseos   
  expat.x86_64                                                                      2.5.0-3.el9_5.3                                                              baseos   
  firefox.x86_64                                                                    128.9.0-2.el9_5                                                              appstream
  freetype.x86_64                                                                   2.10.4-10.el9_5                                                              baseos   
  kernel.x86_64                                                                     5.14.0-503.35.1.el9_5                                                        baseos   
  kernel-core.x86_64                                                                5.14.0-503.35.1.el9_5                                                        baseos   
  kernel-modules.x86_64                                                             5.14.0-503.35.1.el9_5                                                        baseos   
  kernel-modules-core.x86_64                                                        5.14.0-503.35.1.el9_5                                                        baseos   
  kernel-tools.x86_64                                                               5.14.0-503.35.1.el9_5                                                        baseos   
  kernel-tools-libs.x86_64                                                          5.14.0-503.35.1.el9_5                                                        baseos   
  mesa-dri-drivers.x86_64                                                           24.1.2-3.el9.alma.2                                                          appstream
  mesa-filesystem.x86_64                                                            24.1.2-3.el9.alma.2                                                          appstream
  mesa-libEGL.x86_64                                                                24.1.2-3.el9.alma.2                                                          appstream
  mesa-libGL.x86_64                                                                 24.1.2-3.el9.alma.2                                                          appstream
  mesa-libgbm.x86_64                                                                24.1.2-3.el9.alma.2                                                          appstream
  mesa-libglapi.x86_64                                                              24.1.2-3.el9.alma.2                                                          appstream
  mesa-libxatracker.x86_64                                                          24.1.2-3.el9.alma.2                                                          appstream
  mesa-vulkan-drivers.x86_64                                                        24.1.2-3.el9.alma.2                                                          appstream
  python3-perf.x86_64                                                               5.14.0-503.35.1.el9_5                                                        appstream
  python3-perf.x86_64                                                               5.14.0-503.35.1.el9_5                                                        baseos   
  terraform.x86_64                                                                  1.11.4-1                                                                     hashicorp
  tzdata.noarch                                                                     2025b-1.el9                                                                  baseos   
  webkit2gtk3.x86_64                                                                2.48.1-1.el9_5                                                               appstream
  webkit2gtk3-jsc.x86_64                                                            2.48.1-1.el9_5                                                               appstream
  [hungtx@linux ~]$
  ```
- To update all packages and their dependencies:
  
  `dnf upgrade`
- To update a single package:
  
  `dnf upgrade <package_name>`

## List description and summary information
- Lists description and summary information about installed and available packages:
  
  `dnf info <package_name>`

  ```
  hungtx@linux ~]$ dnf info bpftool.x86_64
  Last metadata expiration check: 0:48:14 ago on Sun 20 Apr 2025 10:08:54 AM CEST.
  Installed Packages
  Name         : bpftool
  Version      : 7.4.0
  Release      : 503.34.1.el9_5
  Architecture : x86_64
  Size         : 3.1 M
  Source       : kernel-5.14.0-503.34.1.el9_5.src.rpm
  Repository   : @System
  From repo    : baseos
  Summary      : Inspection and simple manipulation of eBPF programs and maps
  URL          : https://www.kernel.org/
  License      : ((GPL-2.0-only WITH Linux-syscall-note) OR BSD-2-Clause) AND ((GPL-2.0-only WITH Linux-syscall-note) OR BSD-3-Clause) AND ((GPL-2.0-only WITH
               : Linux-syscall-note) OR CDDL-1.0) AND ((GPL-2.0-only WITH Linux-syscall-note) OR Linux-OpenIB) AND ((GPL-2.0-only WITH Linux-syscall-note) OR MIT) AND
               : ((GPL-2.0-or-later WITH Linux-syscall-note) OR BSD-3-Clause) AND ((GPL-2.0-or-later WITH Linux-syscall-note) OR MIT) AND Apache-2.0 AND BSD-2-Clause AND
               : BSD-3-Clause AND BSD-3-Clause-Clear AND GFDL-1.1-no-invariants-or-later AND GPL-1.0-or-later AND (GPL-1.0-or-later OR BSD-3-Clause) AND (GPL-1.0-or-later
               : WITH Linux-syscall-note) AND GPL-2.0-only AND (GPL-2.0-only OR Apache-2.0) AND (GPL-2.0-only OR BSD-2-Clause) AND (GPL-2.0-only OR BSD-3-Clause) AND
               : (GPL-2.0-only OR CDDL-1.0) AND (GPL-2.0-only OR GFDL-1.1-no-invariants-or-later) AND (GPL-2.0-only OR GFDL-1.2-no-invariants-only) AND (GPL-2.0-only WITH
               : Linux-syscall-note) AND GPL-2.0-or-later AND (GPL-2.0-or-later OR BSD-2-Clause) AND (GPL-2.0-or-later OR BSD-3-Clause) AND (GPL-2.0-or-later OR
               : CC-BY-4.0) AND (GPL-2.0-or-later WITH GCC-exception-2.0) AND (GPL-2.0-or-later WITH Linux-syscall-note) AND ISC AND LGPL-2.0-or-later AND
               : (LGPL-2.0-or-later OR BSD-2-Clause) AND (LGPL-2.0-or-later WITH Linux-syscall-note) AND LGPL-2.1-only AND (LGPL-2.1-only OR BSD-2-Clause) AND
               : (LGPL-2.1-only WITH Linux-syscall-note) AND LGPL-2.1-or-later AND (LGPL-2.1-or-later WITH Linux-syscall-note) AND (Linux-OpenIB OR GPL-2.0-only) AND
               : (Linux-OpenIB OR GPL-2.0-only OR BSD-2-Clause) AND Linux-man-pages-copyleft AND MIT AND (MIT OR GPL-2.0-only) AND (MIT OR GPL-2.0-or-later) AND (MIT OR
               : LGPL-2.1-only) AND (MPL-1.1 OR GPL-2.0-only) AND (X11 OR GPL-2.0-only) AND (X11 OR GPL-2.0-or-later) AND Zlib
  Description  : This package contains the bpftool, which allows inspection and simple
               : manipulation of eBPF programs and maps.
  
  Available Packages
  Name         : bpftool
  Version      : 7.4.0
  Release      : 503.35.1.el9_5
  Architecture : x86_64
  Size         : 2.8 M
  Source       : kernel-5.14.0-503.35.1.el9_5.src.rpm
  Repository   : baseos
  Summary      : Inspection and simple manipulation of eBPF programs and maps
  URL          : https://www.kernel.org/
  License      : ((GPL-2.0-only WITH Linux-syscall-note) OR BSD-2-Clause) AND ((GPL-2.0-only WITH Linux-syscall-note) OR BSD-3-Clause) AND ((GPL-2.0-only WITH
               : Linux-syscall-note) OR CDDL-1.0) AND ((GPL-2.0-only WITH Linux-syscall-note) OR Linux-OpenIB) AND ((GPL-2.0-only WITH Linux-syscall-note) OR MIT) AND
               : ((GPL-2.0-or-later WITH Linux-syscall-note) OR BSD-3-Clause) AND ((GPL-2.0-or-later WITH Linux-syscall-note) OR MIT) AND Apache-2.0 AND BSD-2-Clause AND
               : BSD-3-Clause AND BSD-3-Clause-Clear AND GFDL-1.1-no-invariants-or-later AND GPL-1.0-or-later AND (GPL-1.0-or-later OR BSD-3-Clause) AND (GPL-1.0-or-later
               : WITH Linux-syscall-note) AND GPL-2.0-only AND (GPL-2.0-only OR Apache-2.0) AND (GPL-2.0-only OR BSD-2-Clause) AND (GPL-2.0-only OR BSD-3-Clause) AND
               : (GPL-2.0-only OR CDDL-1.0) AND (GPL-2.0-only OR GFDL-1.1-no-invariants-or-later) AND (GPL-2.0-only OR GFDL-1.2-no-invariants-only) AND (GPL-2.0-only WITH
               : Linux-syscall-note) AND GPL-2.0-or-later AND (GPL-2.0-or-later OR BSD-2-Clause) AND (GPL-2.0-or-later OR BSD-3-Clause) AND (GPL-2.0-or-later OR
               : CC-BY-4.0) AND (GPL-2.0-or-later WITH GCC-exception-2.0) AND (GPL-2.0-or-later WITH Linux-syscall-note) AND ISC AND LGPL-2.0-or-later AND
               : (LGPL-2.0-or-later OR BSD-2-Clause) AND (LGPL-2.0-or-later WITH Linux-syscall-note) AND LGPL-2.1-only AND (LGPL-2.1-only OR BSD-2-Clause) AND
               : (LGPL-2.1-only WITH Linux-syscall-note) AND LGPL-2.1-or-later AND (LGPL-2.1-or-later WITH Linux-syscall-note) AND (Linux-OpenIB OR GPL-2.0-only) AND
               : (Linux-OpenIB OR GPL-2.0-only OR BSD-2-Clause) AND Linux-man-pages-copyleft AND MIT AND (MIT OR GPL-2.0-only) AND (MIT OR GPL-2.0-or-later) AND (MIT OR
               : LGPL-2.1-only) AND (MPL-1.1 OR GPL-2.0-only) AND (X11 OR GPL-2.0-only) AND (X11 OR GPL-2.0-or-later) AND Zlib
  Description  : This package contains the bpftool, which allows inspection and simple
               : manipulation of eBPF programs and maps.
  
  [hungtx@linux ~]$ 
  ```

  ```
  [hungtx@linux ~]$ dnf info bpftool.x86_64 | grep -E 'Packages|Release'
  Installed Packages
  Release      : 503.34.1.el9_5
  Available Packages
  Release      : 503.35.1.el9_5
  [hungtx@linux ~]$ 
  ```
## List
- To list the latest versions of all available packages, including architectures, version numbers, and the repository they were installed from (The @ sign in front of a repository indicates that the package in this line is currently installed):
  
  `dnf list --all`
- command to list only installed packages:
  
  `dnf list --installed`
- command to list all available packages:
  
  `dnf list --available`
- command to list packages for which newer versions are available:
  
  `dnf list --upgrade`

## Install
- To install packages from the repositories:
  
  `dnf install <package_name_1> <package_name_2> ...`

## Remove
- To remove installed packages:
  
  `dnf remove <package_name_1> <package_name_2> ...`

## List transactions - package management history
- To display a list of all the latest DNF transactions:
  
  `dnf history`
- To display a list of all the latest operations for a selected package:
  
  `dnf history list <package_name>`
- To display details of a particular transaction:
  
  `dnf history info <transaction_id>`

## Revert DNF transactions
- To revert the transaction:
  
  `dnf history undo <transaction_id>`
- To revert all DNF transactions performed between a specified transaction and the last transaction:
  
  `dnf history rollback <transaction_id>`


