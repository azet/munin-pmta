PowerMTA Munin Multi Monitor
============================

Portable Bourne shell script. Requires "xpath" (perl).


LICENSE
-------
      Copyright (c) 2011, emarsys eMarketing Systems AG
      All rights reserved.
     
      Redistribution and use in source and binary forms, with or without modification, are permitted provided that  
      the following conditions are met:
     
          Redistributions of source code must retain the above copyright notice, this list of conditions and the  
          following disclaimer. Redistributions in binary form must reproduce the above copyright notice, this list  
          of conditions and the following disclaimer in the documentation and/or other materials provided with the  
          distribution. Neither the name of the emarsys eMarketing Systems AG nor the names of its contributors may  
          be used to endorse or promote products derived from this software without specific prior written permission.
     
      THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, 
      INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE 
      DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, 
      SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR 
      SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,  
      WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE  
      USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


README
------
-> "xpath" cli tool required (if it doesn't ship with your linux distribution run "sudo apt-get install libxml-xpath-perl" or equivalent)
 
-> install:

               o check config (/etc/munin/plugin-conf.d) set "env.REMOTEHOST" and "env.PORT", e.g.:
                 [pmta*]
                       env.REMOTEHOST 127.0.0.1
                       env.PORT 8080

               o chmod +x pmta_

               o link:
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_traffic_in -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_traffic_out -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_conn_in -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_conn_out -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_queue_domains -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_queue_recipients -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-14 14:52 pmta_queue_megabytes -> pmta_
                 lrwxrwxrwx 1 root root    5 2011-11-15 16:31 pmta_top_domains -> pmta_

               o alternative multi-host configuration:
                  you can also link the pmta_ script to various hosts and configure munin to respond 
                  to multiple REMOTEHOSTs, just link pmta_ in this schema and configure munin
                  accordingly - DO NOT USE DOTS IN YOUR IDENTIFIER VARIABLE, USE UNDERSCORE INSTEAD!
                  for example:
                       lrwxrwxrwx 1 root root    5 2011-11-18 12:18 mailhost1_domain_com_pmta_top_domains -> pmta_
                       lrwxrwxrwx 1 root root    5 2011-11-18 12:18 mailhost2_domain_com_pmta_top_domains -> pmta_
                       lrwxrwxrwx 1 root root    5 2011-11-18 12:18 mailhost3_domain_com_pmta_top_domains -> pmta_
                       lrwxrwxrwx 1 root root    5 2011-11-18 12:18 mailhost4_domain_com_pmta_top_domains -> pmta_
                 [...]

                 conf.: 
                  [mailhost1_domain_com_pmta*]
                               env.REMOTEHOST somehostORip
                               env.PORT portnumber
                  [mailhost2_domain_com_pmta*]
                               env.REMOTEHOST someotherhostORip
                               env.PORT portnumber
                 [...]

               o restart munin.

