# Setup Android
## Install

````
dependencies {
    implementation 'com.posthog.android:ablaevent:1.+'
}

````
## Configure

````
public class SampleApp extends Application {
    private static final String POSTHOG_API_KEY = "phc_ySCF4YinUf6DxprJ5B0jXtzgijeTqFkWPsIIfC3yTrC";
    private static final String POSTHOG_HOST = "https://e.abla.io";

    @Override
    public void onCreate() {
        // Create a PostHog client with the given context, API key and host
        PostHog posthog = new PostHog.Builder(this, POSTHOG_API_KEY, POSTHOG_HOST)
            .captureApplicationLifecycleEvents() // Record certain application events automatically!
            .recordScreenViews() // Record screen views automatically!
            .build();

        // Set the initialized instance as a globally accessible instance
        PostHog.setSingletonInstance(posthog);

        // Now any time you call PostHog.with, the custom instance will be returned
        PostHog posthog = PostHog.with(this);
    }

````

## Send an Event

````
PostHog.with(this).capture("test-event");

````
