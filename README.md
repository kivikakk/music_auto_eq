# `music_auto_eq`

Helps you manage equaliser settings in Music.app.

## usage

```console
$ ./music_auto_eq help
usage:
  ./music_auto_eq [-f PATH_TO_PLIST]
     list all EQs

  ./music_auto_eq [-f PATH_TO_PLIST] show NAME
     show EQ setting with name NAME

  ./music_auto_eq [-f PATH_TO_PLIST] autoeq [-n] NAME PATH_TO_EQ.TXT [PREAMP_HEADROOM]
     update EQ setting with name NAME using the fixed band EQ
     settings specified.  Defaults to 0.5 dB of headroom.
     Specify -n for a dry run.
     Example input file: https://git.io/JLKUa

I didn't use a proper argument parser so the order of options is non-negotiable.
$
```

## serving suggestion

Let's see what equalisers come with the system:

```console
$ ./music_auto_eq
 #0 Acoustic             [  -0.0 dB]   5.00 dB   4.90 dB   3.95 dB   1.05 dB   2.15 dB   1.75 dB   3.50 dB   4.10 dB   3.55 dB   2.15 dB
 #1 Bass Booster         [  -0.0 dB]   5.50 dB   4.25 dB   3.50 dB   2.50 dB   1.25 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
 #2 Bass Reducer         [  -0.0 dB]  -5.50 dB  -4.25 dB  -3.50 dB  -2.50 dB  -1.25 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
 #3 Classical            [  -0.0 dB]   4.75 dB   3.75 dB   3.00 dB   2.50 dB  -1.50 dB  -1.50 dB   -0.0 dB   2.25 dB   3.25 dB   3.75 dB
 #4 Dance                [  -0.0 dB]   3.57 dB   6.55 dB   4.99 dB   -0.0 dB   1.92 dB   3.65 dB   5.15 dB   4.54 dB   3.59 dB   -0.0 dB
 #5 Deep                 [  -0.0 dB]   4.95 dB   3.55 dB   1.75 dB   1.00 dB   2.85 dB   2.50 dB   1.45 dB  -2.15 dB  -3.55 dB  -4.60 dB
 #6 Electronic           [  -0.0 dB]   4.25 dB   3.80 dB   1.20 dB   -0.0 dB  -2.15 dB   2.25 dB   0.85 dB   1.25 dB   3.95 dB   4.80 dB
 #7 Flat                 [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
 #8 Hip-Hop              [  -0.0 dB]   5.00 dB   4.25 dB   1.50 dB   3.00 dB  -1.00 dB  -1.00 dB   1.50 dB  -0.50 dB   2.00 dB   3.00 dB
 #9 Jazz                 [  -0.0 dB]   4.00 dB   3.00 dB   1.50 dB   2.25 dB  -1.50 dB  -1.50 dB   -0.0 dB   1.50 dB   3.00 dB   3.75 dB
#10 Latin                [  -0.0 dB]   4.50 dB   3.00 dB   -0.0 dB   -0.0 dB  -1.50 dB  -1.50 dB  -1.50 dB   -0.0 dB   3.00 dB   4.50 dB
#11 Loudness             [  -0.0 dB]   6.00 dB   4.00 dB   -0.0 dB   -0.0 dB  -2.00 dB   -0.0 dB  -1.00 dB  -5.00 dB   5.00 dB   1.00 dB
#12 Lounge               [  -0.0 dB]  -3.00 dB  -1.50 dB  -0.50 dB   1.50 dB   4.00 dB   2.50 dB   -0.0 dB  -1.50 dB   2.00 dB   1.00 dB
#13 Piano                [  -0.0 dB]   3.00 dB   2.00 dB   -0.0 dB   2.50 dB   3.00 dB   1.50 dB   3.50 dB   4.50 dB   3.00 dB   3.50 dB
#14 Pop                  [  -0.0 dB]  -1.50 dB  -1.00 dB   -0.0 dB   2.00 dB   4.00 dB   4.00 dB   2.00 dB   -0.0 dB  -1.00 dB  -1.50 dB
#15 R&B                  [  -0.0 dB]   2.62 dB   6.92 dB   5.65 dB   1.33 dB  -2.19 dB  -1.50 dB   2.32 dB   2.65 dB   3.00 dB   3.75 dB
#16 Rock                 [  -0.0 dB]   5.00 dB   4.00 dB   3.00 dB   1.50 dB  -0.50 dB  -1.00 dB   0.50 dB   2.50 dB   3.50 dB   4.50 dB
#17 Small Speakers       [  -0.0 dB]   5.50 dB   4.25 dB   3.50 dB   2.50 dB   1.25 dB   -0.0 dB  -1.25 dB  -2.50 dB  -3.50 dB  -4.25 dB
#18 Spoken Word          [  -0.0 dB]  -3.46 dB  -0.47 dB   -0.0 dB   0.69 dB   3.46 dB   4.61 dB   4.84 dB   4.28 dB   2.54 dB   -0.0 dB
#19 Treble Booster       [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   1.25 dB   2.50 dB   3.50 dB   4.25 dB   5.50 dB
#20 Treble Reducer       [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB  -1.25 dB  -2.50 dB  -3.50 dB  -4.25 dB  -5.50 dB
#21 Vocal Booster        [  -0.0 dB]  -1.50 dB  -3.00 dB  -3.00 dB   1.50 dB   3.75 dB   3.75 dB   3.00 dB   1.50 dB   -0.0 dB  -1.50 dB
$
```

Hmm, looks like the [AutoEQ](https://github.com/jaakkopasanen/AutoEq) project has [some suggestions](https://github.com/jaakkopasanen/AutoEq/tree/60b28289d1724586a333835d1162751e6079d6c6/results/referenceaudioanalyzer/referenceaudioanalyzer_hdm-x_harman_over-ear_2018/Bose%20QuietComfort%2035%20II%20(wireless%2C%20ANC%202)) for the headphones I normally use. Let's try them out.

First, open Music.app and open the **Equaliser** (Window → Equaliser, or <kbd>⌥⌘E</kbd>). Create a new preset by selecting "Make Preset…" from the top of the dropdown menu:

<img width="512" alt="image" src="https://user-images.githubusercontent.com/1915/102851745-bba34f00-4470-11eb-931e-2a39ff3636df.png">

Quit Music.app. You might have to wait a few seconds for it to be saved to disk, but it should eventually appear in the `music_auto_eq` output:

```console
$ ./music_auto_eq
[…]
#15 qc35 II ANC 2        [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
```

The numbers might look different if you had a different EQ preset selected when you created a new one. That's fine.

Now let's try replacing that with the presets from AutoEQ.  Choose the FixedBandEQ.txt variant for your headphones (I'll use [this one](https://github.com/jaakkopasanen/AutoEq/blob/60b28289d1724586a333835d1162751e6079d6c6/results/referenceaudioanalyzer/referenceaudioanalyzer_hdm-x_harman_over-ear_2018/Bose%20QuietComfort%2035%20II%20(wireless%2C%20ANC%202)/Bose%20QuietComfort%2035%20II%20(wireless%2C%20ANC%202)%20FixedBandEQ.txt)) and download it. First we'll try a dry run with `-n`:

```console
$ ./music_auto_eq autoeq -n 'qc35 II ANC 2' 'Bose QuietComfort 35 II (wireless, ANC 2) FixedBandEQ.txt' 
Before: #15 qc35 II ANC 2        [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
 After: #15 qc35 II ANC 2        [ -5.10 dB]  -5.50 dB  -2.70 dB  -2.30 dB  -1.90 dB  -0.70 dB   1.30 dB   0.50 dB   -0.0 dB   4.60 dB  -0.40 dB

dry run, not touching disk
$
```

So far so good! The preamp is calculated to offset the EQ to avoid clipping (per [AutoEQ's readme](https://github.com/jaakkopasanen/AutoEq/blob/60b28289d1724586a333835d1162751e6079d6c6/README.md)); we offset by the highest band adjustment plus 0.5 dB of headroom, but you can configure the headroom by adding it as the last parameter.

Let's say we like this. Drop `-n` and run for realsies:

```console
$ ./music_auto_eq autoeq 'qc35 II ANC 2' 'Bose QuietComfort 35 II (wireless, ANC 2) FixedBandEQ.txt'
Before: #15 qc35 II ANC 2        [  -0.0 dB]   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB   -0.0 dB
 After: #15 qc35 II ANC 2        [ -5.10 dB]  -5.50 dB  -2.70 dB  -2.30 dB  -1.90 dB  -0.70 dB   1.30 dB   0.50 dB   -0.0 dB   4.60 dB  -0.40 dB

backed up /Users/kameliya/Library/Preferences/com.apple.Music.eq.plist to /var/folders/qs/vs29_zxx1qdf7lhmk09sth8r0000gn/T/music_auto_eq.plist20201222-21446-16gqx6r
saved new EQ at /Users/kameliya/Library/Preferences/com.apple.Music.eq.plist
$
```

Fingers crossed it worked! Open Music.app and find out:

<img width="552" alt="image" src="https://user-images.githubusercontent.com/1915/102852235-e5a94100-4471-11eb-8336-c8c38fa756b9.png">

Looks good! Enjoy your EQ!

### disclaimer

`music_auto_eq` tries hard not to eat your plist, but no promises are made. It makes a backup of the target file before overwriting it.

### license

[The Unlicense](https://github.com/kivikakk/music_auto_eq/blob/3036d5b20cbc6326aa4ddd961f1f4d3256c412dc/LICENSE) covers this work.
