
/**
 * seltar's awesome checkbox
 * * custom styling
 * * crossbrowser consistency
 *     IE 7+ (might be able to style it properly for IE 6 and below, but i honestly don't care)
 *     FF 3+
 *     Chrome 14+
 *     Safari 4+
 *     Opera 10+
 *     IOS 3.0+
 *     Android 1.5+
 *     Opera Mobile
 * * support for disabled checkboxes and toggling
 * * keyboard friendly
 * * todo 
 *     aria
 *
 * styling loosely based on this
 * http://www.inserthtml.com/2012/06/custom-form-radio-checkbox/
 */

(function( $ ) {
    $.fn.customCheckbox = function(){
        return this.each(function(){
            var $wrapper = $("<div />").addClass("checkbox-wrapper"),
                $input =  $(this).addClass("checkbox-input"),
                id = $input.attr("id");

            // if the input doesn't have an id, make a random one
            if(!id){
                id = "checkbox_"+Math.round(Math.random()*10000)+"_"+(new Date()).getTime();
                $input.attr("id",id);
            }

            // find the label
            var $label = $("label[for='"+id+"']");
            if($label.length === 0){
                $label = $input.nextAll("label").first();
            }
            // set the correct class
            $label.addClass("checkbox-label");
            // if the label isn't linked with the input, link it
            if(!$label.attr("for")){
                $label.attr("for",id);
            }

            // add the fake checkbox button to replace the checkbox (using a label, it works consistently in all browsers)
            var $link = $label.clone().removeClass("checkbox-label").addClass("checkbox-button").html("<span class='check'>&#x2714;</span>");

            // group them together to add classes to them all
            var $all = $input.add($link).add($label).add($wrapper);

            // mark as checked
            $input.is(":checked") && $all.addClass("checked");
            // mark as disabled
            $input.is(":disabled") && $all.addClass("disabled");

            // bind custom disabled function 
            $input.bind("toggleDisabled",function(e, value){
                $input.prop("disabled",value);
                value && $all.addClass("disabled") || $all.removeClass("disabled");
            });

            // on change, update the checkmark
            $input.change(function(){
                $input.is(":checked") && $all.addClass("checked") || $all.removeClass("checked");
                return true;
            });

            // fix for ios < 6
            $label.get(0).onclick = function(){};
            $link.get(0).onclick = function(){};

            // insert wrapper before input
            $input.before($wrapper);
            // insert input, button and label into wrapper
            $wrapper.append($input,$link,$label);
        });
    };
})( jQuery );
