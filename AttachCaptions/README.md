# Attach Captions for CumulusClips

This is a plugin to allow users to upload and attach .vtt and .srt files to their videos in the CumulusClips application.  

# Installation

## Adding a trigger to the Attachments area of the video editor

After installing, you will need to place the relevant code into your theme.  For example, you might start around line 99 of the default theme file account/videos_edit.phtml.  Adding the following trigger there allows the plugin to format attachment form elements as needed:

```php
            <div class="upload-progress">

                                        <a class="remove" href=""><span class="glyphicon glyphicon-remove"></span></a>
                                                                    <span class="title"><?php echo $file[0]->name; ?> (<?php echo \Functions::              formatBytes($file[0]->filesize,0); ?>)</span>

                                                                                                <span class="pull-right glyphicon glyphicon-ok"> </span>
                                                                                                                            <?php Plugin::triggerEvent( 'videos.edit.attachment.list', $file[0]->fileId, $video-    >videoId ); ?>

                                                                                                                                                    </div>
                        </div>
```

### Adding captions to the default HTML5 player

The above change will let you set default caption files.  To get your player to pick these up, you may need to edit the various embed code appropriately.  So, somewhere in a video element you could do this:

```php
<?= Plugin::triggerFilter('theme.watch.attachment.captions', $video->videoId); ?>
```
