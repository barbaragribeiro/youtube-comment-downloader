# youtube-comment-downloader
Simple script for downloading Youtube comments without using the Youtube API. The output is in line delimited JSON.

### Dependencies
* Python 2.7+
* requests
* lxml
* cssselect

The python packages can be installed with

    pip install requests
    pip install lxml
    pip install cssselect

### Usage
```
usage: downloader.py [--help] [--youtubeid YOUTUBEID | --input INPUT] [--output OUTPUT]

Download Youtube comments without using the Youtube API

optional arguments:
  --help, -h            Show this help message and exit
  --youtubeid YOUTUBEID, -y YOUTUBEID
                        ID of Youtube video for which to download the comments
  --input INPUT, -i INPUT
                        Input filename (a file containing video IDs, one ID per line)
  --output OUTPUT, -o OUTPUT
                        Output filename (output format is line delimited JSON).
			If comments are being downloaded for multiple videos (through -i)
			this should be a template with "id" as a key. See examples below
```

For example:
```
python downloader.py --youtubeid ScMzIvxBSi4 --output ScMzIvxBSi4.json

#Download comments for each video in videos.txt and save each output under your/path directory
python downloader.py --input video_ids.txt --output 'your/path/%(id)s.json'


#Download comments for each video in videos.txt and save the output in a comments.json file under a separate directory for each video
python downloader.py --input video_ids.txt --output '%(id)s/comments.json'
```

For Youtube IDs starting with - (dash) you will need to run the script with:
`-y=-idwithdash` or `--youtubeid=-idwithdash`
