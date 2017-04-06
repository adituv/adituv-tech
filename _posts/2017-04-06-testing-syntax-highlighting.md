---
layout: post
title: Testing Syntax Highlighting
description: Testing Syntax Highlighting in QbScripts
---

{% highlight qbscript %}
script() {

load_songqpak(song_name=(*current_song), async=0);
get_song_struct(song=(*current_song));

if (StructureContains(structure=%song_struct, no_rhythm_track)) {
    change({
        QbKey StructureName = player1_status;
        QbKey Part = guitar;
    });
    
    return {
        QbKey flow_state = quickplay_skip_part_menu_fs;
    };
}

get_song_prefix(song=(*current_song));
FormatText(ChecksumName=song_rhythm_array_id, '%s_song_rhythm_easy', s=%song_prefix);

if (GlobalExists(name=%song_rhythm_array_id, type=array)) {
    GetArraySize(*%song_rhythm_array_id);
    if (%array_size > 0) {
        return {
            QbKey flow_state = quickplay_select_part_fs;
        };
    }
}

if (StructureContains(structure=%song_struct, use_coop_notetracks)) {
    return {
        QbKey flow_state = quickplay_select_part_fs;
    };
}

change({
    QbKey StructureName = player1_status;
    QbKey Part = guitar;
});

return {
    QbKey flow_state = quickplay_skip_part_menu_fs;
};

{% endhighlight %}
