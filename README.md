# sippaudio <!-- omit in toc -->

Run simple SIPp UAS scenario which plays back music after ACK.

- [Running](#running)
- [Preparing music](#preparing-music)

## Running

Run:
```bash
./run_sipp.sh
```

You can modify what port (default is `-p 5080`) and IP SIPp listens on (default is `-i 127.0.0.1`).

With this parameters, your SIP UAC should call `100@127.0.0.1:5080` (`100` is completely random and is not checked by `uas_music.xml` scenario).

## Preparing music

Use some `WAV` file as an input. Convert it to `u-law` using `sox` (make sure it is installed):
```bash
sox input.wav --encoding mu-law --bits 8 --rate 8000 -c bach.wav
```

Once conerted, check the format:
```bash
ponyo:sippaudio user$ file bach.wav 
bach.wav: RIFF (little-endian) data, WAVE audio, ITU G.711 mu-law, mono 8000 Hz
ponyo:sippaudio user$ 
```

