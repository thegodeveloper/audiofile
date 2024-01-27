# audiofile
We discuss a command line interface built from scratch which handles generating metadata from uploaded audio files, local flat file storage and retrieval of audio metadata.  This CLI is just an example.  It was created on macOS and other operating systems have not yet been tested at this time.

## To generate the audiofile command line interface:
go build -o audiofile-cli cmd/cli/main.go

## To generate the audiofile API:
go build -o audiofile-api cmd/api/main.go

## Within the root of the audiofile folder, to start the API:
./audiofile-api

### NOTE
To change the default port, 8000, pass in the new port value with the `-p` flag.

## To call the audiofile command line interface:

```shell
./audiofile-cli upload -filename audio/beatdoctor.mp3

Uploading audio/beatdoctor.mp3 ...
Audiofile ID:  56db4987-aa88-4c43-8dd5-6558ae213a7c
```

This command creates a directory called audiofile in the user's home directory.

## Get file ID

```shell
./audiofile-cli get -id 56db4987-aa88-4c43-8dd5-6558ae213a7c

{
    "Id": "56db4987-aa88-4c43-8dd5-6558ae213a7c",
    "Path": "/Users/william/audiofile/56db4987-aa88-4c43-8dd5-6558ae213a7c/beatdoctor.mp3",
    "Metadata": {
        "tags": {
            "title": "Shot In The Dark",
            "album": "Best Bytes Volume 4",
            "artist": "Beat Doctor",
            "album_artist": "Toucan Music (Various Artists)",
            "composer": "",
            "genre": "Electro House",
            "year": 0,
            "lyrics": "",
            "comment": "URL: http://freemusicarchive.org/music/Beat_Doctor/Best_Bytes_Volume_4/09_beat_doctor_shot_in_the_dark\r\nComments: http://freemusicarchive.org/\r\nCurator: Toucan Music\r\nCopyright: Attribution-NonCommercial 3.0 International: http://creativecommons.org/licenses/by-nc/3.0/"
        },
        "transcript": ""
    },
    "Status": "Complete",
    "Error": null
}
```

## Testing

```shell
go test ./cmd/cli/command -v

```