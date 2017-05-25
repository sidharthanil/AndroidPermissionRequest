# AndroidPermissionRequest
A static java class to request run time permissions in android


Usage:

In your activity class check for permission using any of the static functions provided

Say i want to check location access

```

if(PermissionCheck.islocationAccessAvailable(Activity.this){
  // if true do what you have to do
} else {
  //request for permissions. You can automate this process if you want by modifying the static class
  PermissionCheck.requestLocationPermission(Activity.this);
}

```

In your activity class, inside your onRequestPermissionsResult() do this to properly receive yout permission

```

  @Override
      public void onRequestPermissionsResult(int requestCode,
                                           String permissions[], int[] grantResults) {
        switch (requestCode) {
            case PermissionCheck.MY_PERMISSIONS_REQUEST_LOCATION: {
                for (int i = 0; i < permissions.length; i++) {
                    int grantResult = grantResults[i];
                    if (grantResult == PackageManager.PERMISSION_GRANTED) {
                        return;
                    }
                }
                break;
            }
            default:
                break;
            // other 'switch' lines to check for other
            // permissions this app might request
        }
    }
    
    
```
    
    
    


