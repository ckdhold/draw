## Operation Steps

1. On first entry, no data will be displayed. You can choose to use default data to see the overall display effect. It is recommended to import your own data for operation. Steps are as follows:

    a. In Personnel Configuration - Personnel List - Download Template, download the data template and modify it to fill in the data (please note that the header cannot be modified).

    b. After modification, click 'Upload File' on the same page to upload the modified Excel file.

2. Enter Prize Configuration to modify your prize information. Keep the name as short as possible for easy display; "Is All Participants" means whether this prize is drawn from all personnel (those who have already won can still participate); "Number of Winners" refers to the number of people to be drawn for this prize; "Number of Winners" is not editable; "Drawn" means this prize has been used when selected, unchecking will reset the prize but will not reset the winners; the picture is the prize image displayed on the homepage (you can upload it yourself in the image list); the left icon is used to adjust the prize order.

Completing the above two items is sufficient for normal use.

## Function Description

1. Add temporary lottery: There is a '+' button in the prize list on the lottery page. Click to add a temporary lottery. Note: Only one temporary lottery can be added at a time. After successful addition, the current prize is set to this temporary prize. After successful drawing, it returns to the normal prize list.
2. Music and image list, you can upload your own files for use. After the image is successfully uploaded, you can select the image to display in the prize configuration, and after the music is successfully uploaded, it is added to the playlist.
3. Music playback: Click with the left mouse button to play/pause, click with the right mouse button to play the next song.
4. In Interface Configuration - Pattern Settings, you can use the mouse to click to customize the highlight pattern on the homepage.
5. If you don't want to display the prize list on the homepage, select 'Always Show Prize List' in Interface Configuration.
6. When clicking the button on the homepage, the button value will not be updated immediately, it will be updated to the target value after the animation ends, which is a normal phenomenon.

## Shortcut Keys

Shortcut keys are set on the lottery page.

| Shortcut Key | Description |
| --- | --- |
| Space | Enter lottery/Start/Draw lucky winner/Continue |
| Esc | Cancel |

## Lottery Algorithm

This project uses a random algorithm for lottery to ensure fairness:

- **Non-repetitive random sampling**: Uses `Math.random()` to generate random indices, ensuring each participant has an equal probability of being drawn
- **No replacement after drawing**: Winners are removed from the personnel pool to ensure no duplicate wins
- **Dynamic personnel pool**: The personnel pool dynamically shrinks after each draw to ensure fairness in subsequent draws
- **Support for batch drawing**: Supports dividing prizes into multiple batches for drawing, flexible configuration