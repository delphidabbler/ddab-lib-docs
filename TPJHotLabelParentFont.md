#summary Description of the TPJHotLabel.ParentFont property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ParentFont property =

*Project:* [HotLabelComponent Hot Label Component].

*Unit:* _PJHotLabel_.

*Class:* _[TPJHotLabel TPJHotLabel]_

{{{
property ParentFont: Boolean;
}}}

== Description ==

This property determines where a control looks for its font information.

To have the component use the same font in its _[TPJHotLabelFont Font]_ property as its parent control, set _!ParentFont_ to `True`.

Normally _!ParentFont_ is set to `True` for all controls in order to ensure that all the controls on a form have a uniform appearance. For example, if _!ParentFont_ is `True` for all controls in a form, changing the form's _Font_ property to 12 point Courier causes all controls on the form to use that font.

Changing this component's _[TPJHotLabelFont Font]_ property causes _!ParentFont_ to be set to `False` automatically.

The _!ParentFont_ property of _[TPJHotLabel TPJHotLabel]_ defaults to `False` since the default attributes of the _[TPJHotLabelFont Font]_ property differ from the parent control in order to make the hot-link stand out.
