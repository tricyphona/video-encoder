# Video Encoder

A simple media encoder build in Python using ffmpeg

## How to install

Make sure that Python 2.7 or 3.6 are installed. 


## Usage

1. Execute the `Server.py` script.
2. Add Files to the Media folder.
3. Wait for the file to be encoded.
4. grap the new file from the `Media Destination Folder`.
5. Press 'q' to stop the script


## Config settings

An overview of the current Config file.
```json
{
    "Folder":
    {
        "Media Folder": "Media/",
        "Media Destination Folder": "MediaDestinationFolder/",
        "Garbage Folder": "GarbageFolder/"
    },
    "Aproved Extension":
        {
           "Extension":"[mp4]" 
        },
    "VideoEncoder":
        {
            "Vcodec": "libx264",
            "Fps": "59.94",
            "encoding": "veryslow",
            "Resolution":"1920:1080",
            "Bitrate":"12M",
            "Buffer":"24M"

        },
    "AudioEncoder": {
        "Acodec": "aac",
        "Bitrate": "256k",
		"LUFS Encoding":true,
		"Integrated Loudness":"-23",
		"Integrated Loudness+-":"-1",
		"Maximum loudness range":"20"
    }
}
```

`Media Folder` is the folder all new videos needs to go in to.
`Media Destination Folder` is the folder all the encoded videos are being saved at.
`Garbage Folder` is the folder the original files go to after the encoding is done.
```json
{
    "Folder":
    {
        "Media Folder": "Media/",
        "Media Destination Folder": "MediaDestinationFolder/",
        "Garbage Folder": "GarbageFolder/"
    }
}
```

All Aproved Extensions goes in here. `[mp4, mov, ....]`
```json
{
    "Aproved Extension":
        {
           "Extension":"[mp4]" 
        }
}
```

In the videoEncoder setting, the `Buffer` has to be twice the size of the bitrate.
The encoder is set to do CBR (Constant Bit Rate).
```json
{
    "VideoEncoder":
        {
            "Vcodec": "libx264",
            "Fps": "59.94",
            "encoding": "veryslow",
            "Constant Rate Factor":"18",
            "Resolution":"1920:1080",
            "Bitrate":"12M",
            "Buffer":"24M"
        }
}
```


##LUFS

The script use the build in linear normalization. see 7.70 loudnorm in https://ffmpeg.org/ffmpeg-filters.html#loudnorm
this function use:
I, Set integrated loudness target. Range is -70.0 - -5.0. Default value is -23.0.

LRA, Set loudness range target. Range is 1.0 - 20.0. Default value is 20.0.

TP, Set maximum true peak. Range is -9.0 - +0.0. Default value is -3.0.



## Log

The encoder try to log as much as possible.
