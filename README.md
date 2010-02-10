  midi-clj
==============

#### A streamlined midi API for Clojure

midi-clj is being developed for Project Overtone, and it is meant to simplify
the usage of midi devices and the midi system from within Clojure.

    (use 'midi)
    
    ; Select midi input and output devices
    ; These functions bring up a GUI chooser window to select a midi port
    (def keyboard (midi-in))
    (def phat-synth (midi-out))

    ; Once you know the correct device names for your devices you can save the
    ; step of opening up the GUI chooser by putting a unique part of the name 
    ; as an argument to midi-in or midi-out.  The first device with a name that
    ; matches with lookup is returned.
    (def ax (midi-in "axiom"))
    
    ; Connect ins and outs easily
    (midi-route keyboard phat-synth)
    
    ; Trigger a note (note 40, velocity 100)
    (midi-note-on phat-synth 40 100)
    (Thread/sleep 500)
    (midi-note-off phat-synth 0)
    
    ; Or the short-hand version to start and stop a note
    (midi-note phat-synth 40 100 500)
    
    ; And the same thing with a sequence of notes
    (midi-play phat-synth [40 47 40] [80 50 110] [250 500 250])

In Ubuntu Linux I use the snd-virmidi kernel module to provide software midi
ports.  USB midi devices should be pretty much plug and play.


### Project Info:

#### Source Repository
Downloads and the source repository can be found on GitHub:

  http://github.com/rosejn/midi-clj

Eventually there will be more documentation for this library, but in the
meantime you can see it in use within the context of Project Overtone, located
here:

  http://github.com/rosejn/overtone

#### Mailing List

For any questions, comments or patches, use the Overtone google group here:

http://groups.google.com/group/overtone

### Authors

* Jeff Rose
