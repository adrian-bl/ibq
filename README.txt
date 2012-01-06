WHAT IS ibq?
--------------------------------------------------------
ibq will try to convert the output of 'ibnetdiscover -v'
into an ascii-art image of your physical switch.


FEATURES OF ibq
--------------------------------------------------------
 * ibq was written for use with the Sun/Oracle DCS648
   switch. The script will even display the correct 
   cable color if used with this switch
 
 * Multiple switches can be connected to the DCS648, ibq
   will simply add all hosts on the 'other' switch to the
   uplink port


BUGS OF ibq
--------------------------------------------------------
 * The Switch Detection is broken (use --forceswitch)
 * ibq will probably fail if you have a complex setup
   with multiple paths to the same switch


LICENSE OF ibq
--------------------------------------------------------
 * 'ibq' is licensed under the GPLv2 (only)


USAGE
--------------------------------------------------------

The '--matrix' option will display an ascii-art image
of the switch:

Guessed switch model:  >Oracle(R)(TM) 648(R) QDR(R) ...
####|       0       |       1       |       2       |..
 8A |a6226a6227a6228|a6213a6224a6225|a6220a6221a6222|..
 8B |a6229a6269a6309|a6260a6261a6262|a6263a6264a6265|..
 7A |a6380a6381a6382|a6383a6384a6385|a6349a6389a6429|..

This makes it easy to spot 'holes' and to identify 
hosts. Eg: a6227 is connected to port 8A0


The '--host' option can be used to display information 
about a single host:

 ./ibq --host a6227
# >> connections of a6227 <<
# a6227 port=1 > 0x212800013e40f6 links to 0x21283a856a18a2 (port=21)
 linecard guid          = 0x21283a856a1800
 switch-chip index      = 0 (0xa2)
 on-chip index          = 2 (0x15)
 physical linecard id   = 8
 linecard row           = A
 linecard port          = 0
 cable color            = [    y    ]
 direct connection      = yes
 switchport of a6227:1  = 8A0


a6227 has a 'direct' connection to the detected
switch and uses a yellow cable plugged into 8A0
