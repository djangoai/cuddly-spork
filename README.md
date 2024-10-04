<script>

  {# You’ll need to `import hmac` and `import hashlib` #}
  window.intercomSettings = {
    api_base: "https://api-iam.intercom.io",
    app_id: "ydga7bhi",
    user_id: "{{ request.user.id|escapejs }}", // a UUID for your user
    user_hash: "{{
      hmac.new(
        b'mA0b1XsFeFLFU03__pGOx3r9ZDi0BwqRvb76Gk83',
        bytes(request.user.id, encoding='utf-8'),
        digestmod=hashlib.sha256
      ).hexdigest()
    }}" // an Identity Verification user hash for your user
  };
</script>

<script>
// We pre-filled your app ID in the widget URL: 'https://widget.intercom.io/widget/ydga7bhi'
(function(){var w=window;var ic=w.Intercom;if(typeof ic==="function"){ic('reattach_activator');ic('update',w.intercomSettings);}else{var d=document;var i=function(){i.c(arguments);};i.q=[];i.c=function(args){i.q.push(args);};w.Intercom=i;var l=function(){var s=d.createElement('script');s.type='text/javascript';s.async=true;s.src='https://widget.intercom.io/widget/ydga7bhi';var x=d.getElementsByTagName('script')[0];x.parentNode.insertBefore(s,x);};if(document.readyState==='complete'){l();}else if(w.attachEvent){w.attachEvent('onload',l);}else{w.addEventListener('load',l,false);}}})();
</script>









import hmac
import hashlib

hmac.new(
  b'mA0b1XsFeFLFU03__pGOx3r9ZDi0BwqRvb76Gk83', # an Identity Verification secret key (web)
  bytes(request.user.id, encoding='utf-8'), # a UUID to identify your user
  digestmod=hashlib.sha256 # hash function
).hexdigest()