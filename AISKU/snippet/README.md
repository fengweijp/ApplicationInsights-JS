<properties
	pageTitle="Application Insights JavaScript SDK - Snippets"
	description="Reference doc"
	services="application-insights"
    documentationCenter=".net"
/>

<tags
	ms.service="application-insights"
	ms.workload="tbd"
	ms.tgt_pltfrm="ibiza"
	ms.devlang="na"
	ms.topic="article"
	ms.date="8/28/2020"/>

# Microsoft Application Insights JavaScript SDK - Snippet Injection

## How to push Application Insights JS snippet changes consumed by Application Insights dotnet package.

1.  Fork Application Insights dotnet [Repo](https://github.com/microsoft/ApplicationInsights-dotnet).
2.  Get the latest copy of JS snippet and make changes in NETCORE\src\Microsoft.ApplicationInsights.AspNetCore\Resources.resx file.

### Build/Test Changes:
1. Open Everything.sln file. Run build and Tests on AspNetCore project

### Test Changes Locally:

1. Create a dot net [SampleWebApp](https://docs.microsoft.com/en-us/visualstudio/ide/quickstart-aspnet-core?view=vs-2019).
2.  Open your SampleWebApp and enable client side telemetry. More details on how to do this [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/asp-net-core#enable-client-side-telemetry-for-web-applications)
3.  In SampleWebApp\Startup.cs configure ikey
4.  In SampleWebApp\WebApplication1.csproj Refer the package Microsoft.ApplicationInsights.AspNetCore you just build from the build output folder: \your visual studio workspace\bin\Debug\NuGet.

## How to inject Javascript with Sharepoint Framework Extensions through [Snippet Setup](https://github.com/microsoft/ApplicationInsights-JS/tree/master/SPO#snippet-setup-ignore-if-using-npm-setup)

Due to security concerns, you can't directly add the script that's described in [this](https://docs.microsoft.com/en-us/azure/azure-monitor/app/sharepoint) article to your webpages in the SharePoint modern UX. As an alternative, you can use [SharePoint Framework (SPFx)](/sharepoint/dev/spfx/extensions/overview-extensions) to build a custom extension that you can use to install Application Insights on your SharePoint sites. There are two ways to add Application Insights to your extension solution, either install via NPM setup or drop a script tag on the extension head. If you choose the second option, see How to create a SPFx extension solution with AppInsights installed from scratch [Snippet Setup](https://github.com/microsoft/ApplicationInsights-JS/tree/master/SPO#snippet-setup-ignore-if-using-npm-setup) section or [view the sample](https://github.com/microsoft/ApplicationInsights-JS/tree/master/SPO/AppInsightsExtensionSolutionSample-Snippet). 

- Snippet for SPO modern UX scenario: 
```js
`!function(T,l,y){var S=T.location,u="script",k="instrumentationKey",D="ingestionendpoint",C="disableExceptionTracking",E="ai.device.",I="toLowerCase",b="crossOrigin",w="POST",e="appInsightsSDK",t=y.name||"appInsights";(y.name||T[e])&&(T[e]=t);var n=T[t]||function(d){var g=!1,f=!1,m={initialize:!0,queue:[],sv:"4",version:2,config:d};function v(e,t){var n={},a="Browser";return n[E+"id"]=a[I](),n[E+"type"]=a,n["ai.operation.name"]=S&&S.pathname||"_unknown_",n["ai.internal.sdkVersion"]="javascript:snippet_"+(m.sv||m.version),{time:function(){var e=new Date;function t(e){var t=""+e;return 1===t.length&&(t="0"+t),t}return e.getUTCFullYear()+"-"+t(1+e.getUTCMonth())+"-"+t(e.getUTCDate())+"T"+t(e.getUTCHours())+":"+t(e.getUTCMinutes())+":"+t(e.getUTCSeconds())+"."+((e.getUTCMilliseconds()/1e3).toFixed(3)+"").slice(2,5)+"Z"}(),iKey:e,name:"Microsoft.ApplicationInsights."+e.replace(/-/g,"")+"."+t,sampleRate:100,tags:n,data:{baseData:{ver:2}}}}var h=d.url||y.src;if(h){function a(e){var t,n,a,i,r,o,s,c,p,l,u;g=!0,m.queue=[],f||(f=!0,t=h,s=function(){var e={},t=d.connectionString;if(t)for(var n=t.split(";"),a=0;a<n.length;a++){var i=n[a].split("=");2===i.length&&(e[i[0][I]()]=i[1])}if(!e[D]){var r=e.endpointsuffix,o=r?e.location:null;e[D]="https://"+(o?o+".":"")+"dc."+(r||"services.visualstudio.com")}return e}(),c=s[k]||d[k]||"",p=s[D],l=p?p+"/v2/track":config.endpointUrl,(u=[]).push((n="SDK LOAD Failure: Failed to load Application Insights SDK script (See stack for details)",a=t,i=l,(o=(r=v(c,"Exception")).data).baseType="ExceptionData",o.baseData.exceptions=[{typeName:"SDKLoadFailed",message:n.replace(/\\./g,"-"),hasFullStack:!1,stack:n+"\\nSnippet failed to load ["+a+"] -- Telemetry is disabled\\nHelp Link: https://go.microsoft.com/fwlink/?linkid=2128109\\nHost: "+(S&&S.pathname||"_unknown_")+"\\nEndpoint: "+i,parsedStack:[]}],r)),u.push(function(e,t,n,a){var i=v(c,"Message"),r=i.data;r.baseType="MessageData";var o=r.baseData;return o.message='AI (Internal): 99 message:"'+("SDK LOAD Failure: Failed to load Application Insights SDK script (See stack for details) ("+n+")").replace(/\\"/g,"")+'"',o.properties={endpoint:a},i}(0,0,t,l)),function(e,t){if(JSON){var n=T.fetch;if(n&&!y.useXhr)n(t,{method:w,body:JSON.stringify(e),mode:"cors"});else if(XMLHttpRequest){var a=new XMLHttpRequest;a.open(w,t),a.setRequestHeader("Content-type","application/json"),a.send(JSON.stringify(e))}}}(u,l))}function i(e,t){f||setTimeout(function(){!t&&m.core||a()},500)}var e=function(){var n=l.createElement(u);n.src=h;var e=y[b];return!e&&""!==e||"undefined"==n[b]||(n[b]=e),n.onload=i,n.onerror=a,n.onreadystatechange=function(e,t){"loaded"!==n.readyState&&"complete"!==n.readyState||i(0,t)},n}();y.ld<0?l.getElementsByTagName("head")[0].appendChild(e):setTimeout(function(){l.getElementsByTagName(u)[0].parentNode.appendChild(e)},y.ld||0)}try{m.cookie=l.cookie}catch(p){}function t(e){for(;e.length;)!function(t){m[t]=function(){var e=arguments;g||m.queue.push(function(){m[t].apply(m,e)})}}(e.pop())}var n="track",r="TrackPage",o="TrackEvent";t([n+"Event",n+"PageView",n+"Exception",n+"Trace",n+"DependencyData",n+"Metric",n+"PageViewPerformance","start"+r,"stop"+r,"start"+o,"stop"+o,"addTelemetryInitializer","setAuthenticatedUserContext","clearAuthenticatedUserContext","flush"]),m.SeverityLevel={Verbose:0,Information:1,Warning:2,Error:3,Critical:4};var s=(d.extensionConfig||{}).ApplicationInsightsAnalytics||{};if(!0!==d[C]&&!0!==s[C]){method="onerror",t(["_"+method]);var c=T[method];T[method]=function(e,t,n,a,i){var r=c&&c(e,t,n,a,i);return!0!==r&&m["_"+method]({message:e,url:t,lineNumber:n,columnNumber:a,error:i}),r},d.autoExceptionInstrumented=!0}return m}(y.cfg);(T[t]=n).queue&&0===n.queue.length&&n.trackPageView({})}(window,document,{
            src: "https://az416426.vo.msecnd.net/scripts/b/ai.2.gbl.min.js", // The SDK URL Source
            //name: "appInsights", // Global SDK Instance name defaults to "appInsights" when not supplied
            //ld: 0, // Defines the load delay (in ms) before attempting to load the sdk. -1 = block page load and add to head. (default) = 0ms load after timeout,
            //useXhr: 1, // Use XHR instead of fetch to report failures (if available),
            crossOrigin: "anonymous", // When supplied this will add the provided value as the cross origin attribute on the script tag 
            cfg: { // Application Insights Configuration
                instrumentationKey: "` + this.properties.instrumentationKey + `"
            }});`
```