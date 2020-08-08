<template>
  <Layout>
    <Row>
      <Col span="11" class="image__holder">
        <Carousel
          v-model="value3"
          :autoplay="setting.autoplay"
          :autoplay-speed="setting.autoplaySpeed"
          :dots="setting.dots"
          :radius-dot="setting.radiusDot"
          :trigger="setting.trigger"
          :arrow="setting.arrow"
        >
          <CarouselItem>
            <div class="carousel__content">
              <img src="~/assets/image.png" alt="" />
              <div class="note">
                <h3 class="carousel__title">No Hazzles</h3>
                <p class="carousel__text">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                  do eiusmod.
                </p>
              </div>
            </div>
          </CarouselItem>
          <CarouselItem>
            <div class="carousel__content">
              <img src="~/assets/image.png" alt="" />
              <div class="note">
                <h3 class="carousel__title">No Stress</h3>
                <p class="carousel__text">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                  do eiusmod.
                </p>
              </div>
            </div>
          </CarouselItem>
        </Carousel>
      </Col>
      <Col span="13" class="auth__holder">
        <div class="auth__main">
          <div class="auth__content">
            <h2 class="auth__title mb5">Create your free account</h2>
            <p>
              Already registered? <a href="#" class="-color-success">Sign in</a>
            </p>
            <div class="mt-40 my__card">
              <Row :gutter="20">
                <Col span="12">
                  <div>
                    <label for="fname">
                      First Name
                    </label>
                    <div class="form__control">
                      <input
                        id="fname"
                        type="text"
                        class="my__input"
                        placeholder="Joshua"
                      />
                      <img src="~/assets/user.svg" alt="" />
                    </div>
                  </div>
                </Col>
                <Col span="12">
                  <div>
                    <label for="lname">
                      Last Name
                    </label>
                    <div class="form__control">
                      <input
                        id="lname"
                        type="text"
                        class="my__input"
                        placeholder="Bakare"
                      />
                      <img src="~/assets/user.svg" alt="" />
                    </div>
                  </div>
                </Col>
              </Row>
              <Row class-name="mt-40">
                <Col span="24">
                  <div>
                    <label for="email">
                      Email
                    </label>
                    <div class="form__control">
                      <input
                        id="email"
                        type="email"
                        class="my__input"
                        placeholder="josh.bakery@gmail.com"
                      />
                      <img src="~/assets/at.svg" alt="" />
                    </div>
                  </div>
                </Col>
              </Row>
              <Row class-name="mt-40">
                <Col span="24">
                  <div>
                    <label for="pass">
                      Password
                    </label>
                    <div class="form__control">
                      <input
                        id="pass"
                        :type="fieldtype"
                        class="my__input"
                        placeholder="*************"
                      />
                      <Icon
                        ref="iconContainer"
                        class="my__icon"
                        :type="icon"
                        @click="toggleEye"
                      />
                    </div>
                  </div>
                </Col>
              </Row>
              <Row class-name="mt-40">
                <Col class="flex just__right" span="24">
                  <nuxt-link to="/employees" class="my__button">
                    Continue
                  </nuxt-link>
                </Col>
              </Row>
            </div>
          </div>
        </div>
        <div class="text__data">
          <div class="text__content">
            <div>
              <p class="text">
                By siging up, you agree to our
                <a href="#" class="-color-success">Terms</a> and
                <a href="#" class="-color-success">Privacy Policy</a>
              </p>
            </div>
            <div>
              <p class="text">
                © 2019 Tinylabs. All rights reserved.
              </p>
            </div>
          </div>
        </div>
      </Col>
    </Row>
  </Layout>
</template>

<script>
export default {
  data() {
    return {
      value18: '',
      icon: 'ios-eye-outline',
      fieldtype: 'password',
      value3: 0,
      setting: {
        autoplay: true,
        autoplaySpeed: 4000,
        dots: 'inside',
        radiusDot: true,
        trigger: 'click',
        arrow: 'always',
      },
    }
  },
  methods: {
    toggleEye() {
      this.fieldtype = this.fieldtype === 'text' ? 'password' : 'text'
      this.icon =
        this.icon === 'ios-eye-outline'
          ? 'ios-eye-off-outline'
          : 'ios-eye-outline'
    },
  },
}
</script>
