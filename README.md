# YouTube Downloader
YouTube Downloader, an open source Android Application that allows you to download videos from YouTube.

<svg xmlns="http://www.w3.org/2000/svg" width="87" height="20"><linearGradient id="b" x2="0" y2="100%"><stop offset="0" stop-color="#bbb" stop-opacity=".1"/><stop offset="1" stop-opacity=".1"/></linearGradient><mask id="a"><rect width="87" height="20" rx="3" fill="#fff"/></mask><g mask="url(#a)"><path fill="#555" d="M0 0h37v20H0z"/><path fill="#4c1" d="M37 0h50v20H37z"/><path fill="url(#b)" d="M0 0h87v20H0z"/></g><g fill="#fff" text-anchor="middle" font-family="DejaVu Sans,Verdana,Geneva,sans-serif" font-size="11"><text x="19.5" y="15" fill="#010101" fill-opacity=".3">build</text><text x="19.5" y="14">build</text><text x="61" y="15" fill="#010101" fill-opacity=".3">passed</text><text x="61" y="14">passed</text></g></svg>
<svg width="120" height="20" font-family="Verdana, sans-serif" xmlns="http://www.w3.org/2000/svg">
        <path fill="#555" d="M110.3956,0H5.0952l-.001.00006H3.49145A3.27386,3.27386,0,0,0,0,2.99988V17a3.27383,3.27383,0,0,0,3.49145,3H110.3956c2.814,0,5.0952-1.34314,5.0952-3V3C115.4908,1.34314,113.20957,0,110.3956,0Z"/><g fill="#fff" transform="translate(0,0.7)">
      <path d="M7.41141,8.86628A3.96487,3.96487,0,0,1,9.25305,6.46449L8.4039,4.99788A5.66287,5.66287,0,0,0,5.7725,8.42876Z"/>
      <path d="M10.20919,6.06776a3.97645,3.97645,0,0,1,1.02188-.1335l-.00163-1.695a5.66515,5.66515,0,0,0-1.46081.19105Z"/>
      <path d="M12.26155,6.06746a3.964,3.964,0,0,1,2.39894,1.83989L16.129,7.05811a5.66477,5.66477,0,0,0-3.42985-2.62775Z"/>
      <path d="M5.58233,9.89359a5.65418,5.65418,0,0,0,.192,1.46025l1.63816-.43995A3.93459,3.93459,0,0,1,7.27811,9.892l-1.69578.00163Z"/>
      <path d="M6.34169,12.71846a5.66441,5.66441,0,0,0,.89779,1.16644L8.439,12.6859a4.02322,4.02322,0,0,1-.62965-.81668Z"/>
      <path d="M8.41333,14.784a5.6201,5.6201,0,0,0,2.82239.75325l-.00162-1.695a3.93741,3.93741,0,0,1-1.97448-.52729Z"/>
      <path d="M14.66242,11.86693a3.96384,3.96384,0,0,1-2.399,1.84057l.44059,1.63755a5.66624,5.66624,0,0,0,3.42774-2.63189Z"/>
      <path d="M16.69744,11.40093a5.66,5.66,0,0,0,.01008-2.93013l-1.64308.44052a3.95261,3.95261,0,0,1-.009,2.05141Z"/>
    </g><g>
      <text opacity="0.5" x="22" y="15" font-size="11">
        code quality
      </text>
      <text fill="#fff" x="22" y="14" font-size="11">
        code quality
      </text>
    </g><g>
      <path fill="#1bcc1b" d="M114.4026,0h-13.932L100.46986,0H96.98762V20h4V20h13.415a3.26866,3.26866,0,0,0,3.483-3V3A3.26866,3.26866,0,0,0,114.4026,0Z"/>
      <text visibility="hidden">
        A
      </text>
      <path d="M102.80674,13.62617l.69282-.0999,2.95113-8.43367h1.99183l2.9311,8.43367.69282.0999V14.792h-3.30417V13.62617l.67285-.11987-.42635-1.33237h-3.14436l-.42635,1.33237.67286.11987V14.792h-3.30418Zm3.51738-2.88453h2.22494l-1.0925-3.4174h-.03994Z" opacity="0.2"/>
      <path fill="#fff" d="M102.80674,13.17536l.69282-.0999,2.95113-8.43367h1.99183l2.9311,8.43367.69282.0999v1.16581h-3.30417V13.17536l.67285-.11987-.42635-1.33237h-3.14436l-.42635,1.33237.67286.11987v1.16581h-3.30418Zm3.51738-2.88453h2.22494l-1.0925-3.4174h-.03994Z"/>
    </g>
      </svg>


> [Download APK](https://www.codeseasy.com/download/youtube-downloader/)

**Download Function, Download URL is fetched.**

``` 
public void YTDownload(final int itag) {
        String VideoURLDownload = youTubeURL;
        @SuppressLint("StaticFieldLeak") YouTubeUriExtractor youTubeUriExtractor = new YouTubeUriExtractor(this) {
            @Override
            public void onUrisAvailable(String videoId, String videoTitle, SparseArray<YtFile> ytFiles) {
                if ((ytFiles != null)) {
                    String downloadURL = ytFiles.get(itag).getUrl();
                    Log.e("Download URL: ", downloadURL);

                    if (downloadURL != null) {
                        DownloadManager downloadManager = (DownloadManager) getSystemService(DOWNLOAD_SERVICE);
                        DownloadManager.Request request = new DownloadManager.Request(Uri.parse(downloadURL));
                        request.setTitle(videoTitle);
                        request.setDestinationInExternalPublicDir("/Downloads/YouTube-Downloader/", videoTitle + ".mp4");
                        if (downloadManager != null) {
                            downloadManager.enqueue(request);
                        }
                    }
                } else Toast.makeText(MainActivity.this, "Error", Toast.LENGTH_LONG).show();
            }
        };
        youTubeUriExtractor.execute(VideoURLDownload);
    }
```

**onClick for a Button View (Download in Normal Quality)**

```
    public void ytvdownload(View view) {
        youTubeURL = editText.getText().toString();
        if (youTubeURL.contains("http"))
        YouTubeVideoDownloadF(18);
        else Toast.makeText(this,"Enter URL First",Toast.LENGTH_LONG).show();
    }
```

**onClick for a Button View (Download in HD Quality)**
_This option could crash sometimes_
```
    public void ytvdownloadhd(View view) {
        youTubeURL = editText.getText().toString();
        if (youTubeURL.contains("http"))
        YouTubeVideoDownloadF(22);
        else Toast.makeText(this,"Enter URL First",Toast.LENGTH_LONG).show();
    }
```

**Most important Gradle File**
`
implementation 'com.github.HaarigerHarald:android-youtubeExtractor:master-SNAPSHOT'
`

>Created By [Vishnu Sivadas](https://www.vishnusivadas.com)
