# Interaction

This document describes how the various rendering controls are updated
and synchronized.

## Rendering controls

Most of the controls are initialised using the rendering settings
retrieved from the server.


### General controls
 * Save: enabled, if the user has the permissions, when the settings have been changed.
   This needs to be checked against the settings prior to any action. Disabled by default.
 * Save to all: Applies the rendering settings to all the images in the dataset

The following change will trigger a "render" image event and trigger a modification of the
enabled flag of the save button.

 * Undo: undo the last rendering change. Disabled by default
 * Redo: redo the last rendering change. Disabled by default
 * Copy: copy the rendering settings. Enabled by default
 * Paste: paste the copied settings. Disabled by default
    * enabled when settings to paste
    * not enabled for the image the settings are copied from.

 
### Channel controls

The following change will trigger a "render" image event and trigger a modification of the
enabled flag of the save button. 

#### Controls per channel

  * Channel button: this is use to turn a channel on/off. Default value set using the retrieved settings
  * Slider: move left-right knobs to set the input intensity interval. Change update the text fields on both side of the slider. The "render" image is triggered when the knob is released.
  * Text field: set the input intensity interval. Update the slider's value.
  * Color picker: set the color or lut to apply. When a color/lut is applied, the background of the button and the slider are updated

#### Controls for all channels

  * Min/Max: Set the start/end values of the intensity interval to the global min/max.
  global min/max are calculated at import if ``calculate stats`` is on.
  * Full Range: Set the start/end values of the intensity interval to the min/max values of the pixels interval e.g. 0 to 65535 for 16 bit pixels type.
  * Imported: Set the start/end values of the intensity interval to the imported values


## Others users rendering settings

## Histogram

Describe how the UI components are updated when the selection changes.

 * Select "Show histogram" to display the histogram just above the channel.
 * The histogram is displayed for the first active channel.
 * If the first active channel becomes inactive, the histogram corresponding to the 
 next active channel is displayed. If there is no active channel, the histogram is not updated.
 * When the slider knobs are moved or updated by modifying  the values in the start/end text fields, 
   * the vertical bars indicating the input intervals are updated.
   * if the histogram displayed is not the one corresponding to the channel slider. The histogram is first updated.
   * The same applies when the fields are selected
 * Color/lut and histogram update:
    * if the histogram corresponding to the channel is displayed. The color of the histogram is updated.
	* it is not updated if the histogram is not displayed. (Not correct)

