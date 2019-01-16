``` bash
az webapp config container show -g "IgniteTour" -n "msignitetour"
```

``` bash
az webapp config container delete -g "IgniteTour" -n "ignitetour"
```

``` bash
az webapp config container set  -g "IgniteTour" -n "ignitetour" --docker-custom-image-name "microsoft/dotnet-samples:aspnetapp"
```

---

``` bash
az webapp config container set  -g "IgniteTour" -n "msignitetour" --docker-custom-image-name "microsoft/dotnet-samples:aspnetapp"
```

### Convert `Azure Web App` to `Azure Web App for Container`
``` bash
az webapp config container set  -g "IgniteTour" -n "msignitetour" --docker-registry-server-url  "https://index.docker.io"

az webapp config container set  -g "IgniteTour" -n "msignitetour" --docker-custom-image-name "microsoft/dotnet-samples:aspnetapp"
```

### Convert `Azure Web App for Container` to `Azure Web App`
``` bash
az webapp config container delete  -g "IgniteTour" -n "msignitetour"

az webapp config container set  -g "IgniteTour" -n "msignitetour" --docker-custom-image-name "PHP|7.2"
```