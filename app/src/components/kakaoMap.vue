<template>
  <q-page class="flex flex-center">
    <q-item-label header>Open Store</q-item-label>
    <div class="location-icon-area-box">
      <div id="map" style="width: 1620px; height: 1000px;">
      </div>
    </div>
  </q-page>
</template>

<script>
import { onMounted, ref } from 'vue';

export default {
  name: "kakao-map",
  components: {},
  setup() {
    const location = ref(null)
    const loading = ref(false)
    const error = ref(null)
    let map = null
    onMounted(() => {
      userLocationKakaoMap()
    });
    // 현재 위치 가져오기
    const userLocationKakaoMap = () => {
      console.log("Commit test5")
      console.log("(1) Location Mounted!")
      loading.value = true;
      if("geolocation" in navigator) {
        navigator.geolocation.getCurrentPosition(
          (position) => {
            loading.value = false;
            location.value = position;
            console.log("위도 : " , location.value.coords.latitude)
            console.log("경도 : " , location.value.coords.longitude)

            // 위도 & 경도 null이 아닐경우 카카오 맵 로드
            if(location.value.coords.latitude !== null && location.value.coords.longitude !== null) {
              // 카카오 맵 API 로드
              const script = document.createElement('script');
              script.src = `https://dapi.kakao.com/v2/maps/sdk.js?appkey=${process.env.VUE_APP_KAKAO_KEY}&libraries=services&autoload=false`;
              document.head.appendChild(script);
  
              script.onload = () => {
                window.kakao.maps.load(() => {
                  const container = document.getElementById('map');
                  const options = {
                    center: new window.kakao.maps.LatLng(location.value.coords.latitude, location.value.coords.longitude),
                    level: 5, 
                  };
                  console.log("Kakao Map Options : " , options)
                  map = new window.kakao.maps.Map(container, options);

                  const markerPosition = new window.kakao.maps.LatLng(location.value.coords.latitude, location.value.coords.longitude)
                  const marker = new window.kakao.maps.Marker({
                    position: markerPosition,
                    map: map,
                  });
                  const infowindow = new window.kakao.maps.InfoWindow({
                    content: 'Location Information Here', // You can customize this content with your location information
                  });

                  window.kakao.maps.event.addListener(marker, 'click', () => {
                    infowindow.open(map, marker);
                  });
                  // 사용자의 현재 위치 , 이미지를 제공하여 마커를 사용자 정의를 할 수도 있음
                  // const markerImage = new window.kakao.maps.MarkerImage(
                  //   'URL_TO_YOUR_CUSTOM_MARKER_IMAGE',
                  //   new window.kakao.maps.Size(30, 30),
                  // );
                  // const marker = new window.kakao.maps.Marker({
                  //   position: markerPosition,
                  //   map: map,
                  //   image: markerImage, // Use this line if you have a custom marker image
                  // })
                });
              };
            }
          },
          (error) => {
            loading.value = false;
            error.value = `Error getting user location: ${error.message}`;
          }
        );
      }else {
        loading.value = false;
        error.value = "Geolocation is not supported."
      }
    }

    return {
      userLocationKakaoMap
    };
  },
};
</script>