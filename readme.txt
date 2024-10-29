=== bbP Topic Views ===
Contributors: gautamgupta
Donate link: http://bbpep.com/donate/
Tags: views, count, topic views, bbPress, gautam, bbpep
Requires at least: WP 3.3 / bbPress 2.0
Tested up to: WP 3.3.2 / bbPress 2.1
Stable tag: 0.2

Counts the number of times a bbPress topic has been viewed, and allows the administrator to display the count in various places.

== Description ==

bbP Topic Views keeps track of how many times each bbPress topic has been viewed, and then displays the count alongside the title or meta  of the topic on forums pages, topic archive pages, tag pages and view pages.

The plugin is written in such a way that it does not double-count views when a visitor browses to a different page in the same topic. If no view count record exists for a specific topic, the plugin will create a record for it. Rather than setting the initial view count to zero, the plugin sets it to the number of posts in the topic, because it has obviously been viewed at least as many times as people have posted in it!  This is especially nice for adding the plugin to existing bbPress forums so the view count isn't zero for every single topic.

The plugin also offers you some functions, which you can call in your template to output the topic view count and some shortcodes which you can place in your posts to generate a topic table for most viewed topics (see [Other Notes](http://wordpress.org/extend/plugins/bbp-topic-views/other_notes)). As you might have guessed till now, there is also a view for the same.

This plugin is a fork of [_ck_](http://bbshowcase.org/) and wittmania's [bb Topic Views](http://bbpress.org/plugins/topic/bb-topic-views/) plugin for bbPress standalone. Many thanks to them!

== Installation ==

1. Install in your plugins folder and activate.
2. Go to `Settings` -> `Forums` -> (scroll down to) `bbP Topic Views` and
configure the settings.

== Other Notes ==

= Shortcode =
 * `[bbp-single-view id="btv-most-viewed"]` to generate a topic table for most viewed topics.

= Function Calls =
* `$bbp->shortcodes->display_view( array( 'id' => 'btv-most-viewed' ) );` to generate a topic table for most viewed topics.
* `btv_topic_view_count( $topic_id )` or
* `btv_get_topic_view_count( $topic_id )` to output or retrieve the view counts for the supplied topic id (optional, if not passed, it is guessed by using the `bbp_get_topic_id()` function).

To add a view count column to front page, forum, and/or tags page tables, make the following modifications. *Note*: these apply to the default bbPress (TwentyTen) theme. If you are using a different theme, or a highly modified version of the default, your modifications may be slightly different. It is recommended if you make a [child theme](http://codex.wordpress.org/Child_Themes/) of your theme before following these steps so that when you upgrade bbPress or your theme, your changes are not lost.

1. Go to `Admin Section` -> `Settings` -> `Forums` -> (scroll down to) `bbP Topic Views` and check the add nowhere option. This will prevent the view count from being added anywhere automatically.
2. Open `your-theme-name/bbpress/loop-topics.php`. Around line 17, you would find:
`<th class="bbp-topic-title"><?php _e( 'Topic', 'bbpress' ); ?></th>
<th class="bbp-topic-voice-count"><?php _e( 'Voices', 'bbpress' ); ?></th>`
Replace it with:
`<th class="bbp-topic-title"><?php _e( 'Topic', 'bbpress' ); ?></th>
<th class="bbp-topic-view-count"><?php _e( 'Views', 'bbpress' ); ?></th>
<th class="bbp-topic-voice-count"><?php _e( 'Voices', 'bbpress' ); ?></th>`

Around line 71, you would find:
`<td class="bbp-topic-voice-count"><?php bbp_topic_voice_count(); ?></td>`
Replace it with:
`<td class="bbp-topic-view-count"><?php btv_topic_view_count(); ?></td>
<td class="bbp-topic-voice-count"><?php bbp_topic_voice_count(); ?></td>`

You can rearrange the order of the columns if you'd like, just make sure you get them in the right order for each section.

= Translations =
 * Italian by [Alex](http://it.3ddsaddict.com/)

= Donate =
You may donate by going [here](http://bbpep.com/donate/).

= Todo =
Nothing for now.

== Frequently Asked Questions ==

= What is required to run this? =
You should be running WordPress 3.3+ and [bbPress](http://wordpress.org/extend/plugins/bbpress/) 2.0+.

== Screenshots ==

1. Most Viewed View
2. Settings Section

== Changelog ==

= 0.2 (2011-10-7) =
 * Fixes the most viewed topics view (thanks to [InterMike](http://www.michealkennedy.com/) for reporting it)
 * Add Italian Translation by [Alex](http://it.3ddsaddict.com/)
 * Some minor fixes which might have resulted in errors or notices
 * l10n/i18n fixes

= 0.1 (2011-08-22) =
 * Initial Release

== Upgrade Notice ==

= 0.2 =
Fixes the most viewed topics view, has some minor & l10n fixes and addition of Italian translation.

= 0.1 =
Initial Release