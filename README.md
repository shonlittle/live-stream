# live-stream

## My live-stream setup

## Setup Media Server

- Sign-up for/log-in to Digital Ocean: https://www.digitalocean.com/
- Create Ant Media Server Enterprise Edition Droplet: https://marketplace.digitalocean.com/apps/ant-media-server-community-edition
  - Check Ant Media cost calculator to determine the size of the server needed: https://antmedia.io/cost-calculator/
  - Setup domain or sub-domain and point it to the Droplet's IP address
- Login to the server.
  - Start/check Ant Media service. Follow the instructions in this video after the installation: https://youtu.be/Hf8vzteVa04?t=126
  - Setup SSL. Instructions: https://www.youtube.com/watch?v=gxkUHyH-WpU
- Login to management portal: https://youtu.be/Hf8vzteVa04?t=142
  - Add new live stream
- Setup OBS: https://youtu.be/Hf8vzteVa04?t=142

## Website

```javascript
// Add third-party dependencies.
import React from "react";
import Iframe from "react-iframe";
import { makeStyles, useMediaQuery, Box, Button } from "@material-ui/core";

// Make styles.
const useStyles = makeStyles((theme) => ({
  title: {
    margin: theme.spacing(1),
  },
  container: { textAlign: "center" },
}));

/**
 * Create component.
 * @param props
 */
const Stream = () => {
  // Styles.
  const classes = useStyles();

  // Mobile
  const mobile = !useMediaQuery("(min-width:1000px)");

  // Live
  const LIVE_APP = "https://domainname:5443/LiveApp/play.html?name=liveAppId";

  // Render component.
  return (
    <Box className={classes.container}>
      <Iframe
        url={LIVE_APP}
        src={LIVE_APP}
        width={mobile ? "256" : "640"}
        height={mobile ? "300" : "360"}
        id="stream-player"
        className="myClassname"
        display="initial"
        position="relative"
        allowFullScreen
        styles={{ display: "block" }}
      />
      <Box>
        <Button onClick={() => window.location.reload()}>
          If you lose the live stream, please try clicking here to refresh the
          browser.
        </Button>
      </Box>
    </Box>
  );
};

// Export component.
export default Stream;
```
