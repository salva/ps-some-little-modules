# Some handy little modules

---

# lib::glob

---

# lib::glob

    !sh
    perl -Mlib::glob=../*/lib script.pl

---

# lib::glob

    !sh
    ~/g/perl/p5-Net-SSH-Any$ ls -d ../*SSH*
    ../p5-Net-OpenSSH         ../p5-Net-OpenSSH-Parallel               ../p5-Net-SSH-Any
    ../p5-Net-OpenSSH-Compat  ../p5-Net-SFTP-Foreign-Backend-Net_SSH2  ../p5-Test-SSH

    ~/g/perl/p5-Net-SSH-Any$ perl -Mlib::glob=../p5-*SSH*/lib t/Net-SSH-Any.t 
    ...
    
---

# Begin

---

# Begin


    !sh
    $ perl -MBegin='$Net::SSH::Any::debug = ~0' t/Net-SSH-Any.t

---

# Begin

    $ perl -Mlib::glob=../*/lib \
           -MNet::SSH::Any \
           -MBegin='$s=Net::SSH::Any->new(localhost); $Net::SSH::Any::debug=-1' \
           -de 1 

    Loading DB routines from perl5db.pl version 1.33
    Editor support available.

    Enter h or `h h' for help, or `man perldebug' for more help.

    main::(-e:1):	1
      DB<1> $s->system(echo => \'/*bin')       
    # stream_encoding: utf8
    # command+args: echo /*bin
    /bin /sbin
    
      DB<2> 


---

# perlrc

---

# perlrc

- perl can be compiled with `-Dusesitecustomize`
- it will run `$sitelib/sitecustomize.pl` before your script
- though, usually, it is disabled
- you can just put your code into a module and load it:

    sh perl -Msetup script.pl

- but anyway...

---

# perlrc

    !sh
    $ perl -Mperlrc t/Net-SSH-Any.t
    # loads ~/.perlrc

    $ perl -Mperlrc=. t/Net-SSH-Any.t
    # loads ./.perlrc

    $ PERL5OPT=-Mperlrc=. perl t/Net-SSH-Any.t

    $ PERL5OPT=-Mperlrc=.:..:../.. perl t/Net-SSH-Any.t


---

# Thanks!