- 👋 Hi, I’m @ikedichukwu123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
ikedichukwu123/ikedichukwu123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import React from 'react';
import { View, StyleSheet } from 'react-native';
import VideoFeed from './components/VideoFeed';

const App = () => {
  return (
    <View style={styles.container}>
      <VideoFeed />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#000',
  },
});

export default App;import React, { useState } from 'react';
import { FlatList, Dimensions, StyleSheet } from 'react-native';
import VideoPlayer from './VideoPlayer';

const videos = [
  { id: '1', url: 'https://www.example.com/video1.mp4' },
  { id: '2', url: 'https://www.example.com/video2.mp4' },
  { id: '3', url: 'https://www.example.com/video3.mp4' },
];

const VideoFeed = () => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const handleScroll = (event) => {
    const index = Math.round(event.nativeEvent.contentOffset.y / Dimensions.get('window').height);
    setCurrentIndex(index);
  };

  return (
    <FlatList
      data={videos}
      renderItem={({ item }) => <VideoPlayer video={item.url} />}
      keyExtractor={(item) => item.id}
      pagingEnabled
      onScroll={handleScroll}
      showsVerticalScrollIndicator={false}
    />
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});

export default VideoFeed;import React from 'react';
import { View, StyleSheet, Dimensions } from 'react-native';
import Video from 'react-native-video';

const VideoPlayer = ({ video }) => {
  return (
    <View style={styles.container}>
      <Video
        source={{ uri: video }}
        style={styles.video}
        resizeMode="cover"
        repeat
        muted
      />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    width: Dimensions.get('window').width,
    height: Dimensions.get('window').height,
  },
  video: {
    width: '100%',
    height: '100%',
  },
});

export default VideoPlayer;
