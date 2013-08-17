AlphaTextView
=============

Changing the Alpha value of an Android TextView pre SDK 11
Taken from:
http://www.gubatron.com/blog/2012/11/30/android-changing-textview-alpha-transparency-across-different-target-sdks/

/**
 * Android devices with SDK below target=11 do not support textView.setAlpha().
 * This is a work around. 
 * @param v - the text view
 * @param alpha - a value from 0 to 255. (0=transparent, 255=fully visible)
 */
public static void setTextViewAlpha(TextView v, int alpha) {
    v.setTextColor(v.getTextColors().withAlpha(alpha));
    v.setHintTextColor(v.getHintTextColors().withAlpha(alpha));
    v.setLinkTextColor(v.getLinkTextColors().withAlpha(alpha));
     
    Drawable[] compoundDrawables = v.getCompoundDrawables();
    for (int i=0 ; i < compoundDrawables.length; i++) {
        Drawable d = compoundDrawables[i];
        if (d != null) {
            d.setAlpha(alpha);
        }
    }
     
}
