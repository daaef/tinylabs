<style scoped>
.layout {
  background: #f6f8f8;
  position: relative;
  overflow: hidden;
  height: 100vh;
}

.layout-header-bar {
  background: #fff;
}

.layout-logo-left {
  width: calc((100%) - (80px));
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  margin: 15px auto;
}

.menu-icon {
  transition: all 0.3s;
}

.rotate-icon {
  transform: rotate(-90deg);
}

.menu-item span {
  display: inline-block;
  overflow: hidden;
  width: 69px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width 0.2s ease 0.2s;
}

.menu-item i {
  transform: translateX(0);
  transition: font-size 0.2s ease, transform 0.2s ease;
  vertical-align: middle;
  font-size: 16px;
}

.collapsed-menu span {
  width: 0;
  transition: width 0.2s ease;
}

.collapsed-menu i {
  transform: translateX(5px);
  transition: font-size 0.2s ease 0.2s, transform 0.2s ease 0.2s;
  vertical-align: middle;
  font-size: 22px;
}
</style>
<template>
  <div class="layout">
    <Header
      :style="{
        padding: '0',
        paddingRight: '40px',
      }"
      class="layout-header-bar"
    >
      <div class="layout-logo">
        <img src="~/assets/logo.svg" alt="" />
      </div>
      <Menu mode="horizontal" active-name="1">
        <Submenu name="3">
          <template slot="title">
            <Avatar icon="" size="large" />
            <span class="avatar__name">Hi, Joshua</span>
          </template>
          <MenuItem name="3-1">Hey</MenuItem>
          <MenuItem name="3-2">I'm</MenuItem>
          <MenuItem name="3-3">Batman</MenuItem>
        </Submenu>
      </Menu>
    </Header>
    <Layout>
      <Sider
        ref="side1"
        v-model="isCollapsed"
        hide-trigger
        collapsible
        :collapsed-width="78"
        :style="{ width: '80px', maxWidth: '80px' }"
      >
        <Menu
          active-name="1-2"
          theme="light"
          width="auto"
          :class="menuitemClasses"
        >
          <MenuItem name="1-1">
            <img src="~/assets/squares.svg" alt="" />
          </MenuItem>
          <MenuItem name="1-2">
            <img src="~/assets/users.svg" alt="" />
          </MenuItem>
          <MenuItem name="1-3">
            <img src="~/assets/card.svg" alt="" />
          </MenuItem>
        </Menu>
      </Sider>
      <Content
        :style="{
          padding: '50px',
          background: 'transparent',
          minHeight: '260px',
        }"
      >
        <div class="employees__layout">
          <h4 class="emp__title">Employees</h4>
          <button class="my__button" @click="toggleAddEmployee">Add New</button>
        </div>

        <div class="employees__card mt-40">
          <div class="employees__layout">
            <h4 class="emp__title2">Josh Bakery Ventures</h4>
            <p>62, Bode Thomas, Surulere, Lagos</p>
          </div>
        </div>
        <transition name="fade">
          <div v-if="show" class="add__employees mt-40">
            <h4 class="emp__title">Add an Employee</h4>
            <Row :gutter="30">
              <Col span="12">
                <div>
                  <label for="fname">
                    First Name
                  </label>
                  <div class="form__control">
                    <input
                      id="fname"
                      v-model="firstname"
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
                      v-model="lastname"
                      type="text"
                      class="my__input"
                      placeholder="Bakare"
                    />
                    <img src="~/assets/user.svg" alt="" />
                  </div>
                </div>
              </Col>
            </Row>
            <Row class-name="mt-40" :gutter="30">
              <Col span="12">
                <div>
                  <label for="email">
                    Email
                  </label>
                  <div class="form__control">
                    <input
                      id="email"
                      v-model="email"
                      type="email"
                      class="my__input"
                      placeholder="josh.bakery@gmail.com"
                    />
                    <img src="~/assets/at.svg" alt="" />
                  </div>
                </div>
              </Col>
              <Col span="12">
                <div>
                  <label for="phone">
                    Phone
                  </label>
                  <div class="form__control">
                    <input
                      id="phone"
                      v-model="phone"
                      type="text"
                      class="my__input"
                      placeholder="+2348012345678"
                    />
                    <img src="~/assets/at.svg" alt="" />
                  </div>
                </div>
              </Col>
            </Row>
            <Row class-name="mt-40">
              <Col class="flex just__right" span="24">
                <button class="my__button" @click="createUser">
                  Submit
                </button>
              </Col>
            </Row>
          </div>
        </transition>
        <div class="employees__actions mt-40">
          <div class="employees__layout">
            <div class="emp__actions">
              <Select
                v-model="model1"
                class="mr-10"
                placeholder="Change role"
                style="width: 200px;"
              >
                <Option
                  v-for="item in role1"
                  :key="item.value"
                  :value="item.value"
                  >{{ item.label }}</Option
                >
              </Select>
              <button class="my__button2 mr-10" @click="onFilterSelect">
                Change
              </button>
              <Select v-model="model11" filterable style="width: 200px;">
                <Option
                  v-for="item in data1"
                  :key="item.value"
                  :value="item.value"
                  placeholder="Enter staff name here…"
                  >{{ item.label }}</Option
                >
              </Select>
            </div>
            <div class="emp__paginator">
              <div>1 of 2</div>
              <div><img src="~/assets/left.svg" alt="" /></div>
              <div><img src="~/assets/right.svg" alt="" /></div>
            </div>
          </div>
        </div>

        <div class="employees__table mt-40">
          <Table
            ref="selection"
            :loading="loading"
            border
            :columns="columns4"
            :data="data1"
          >
            <template slot="name" slot-scope="{ row }">
              <strong>{{ row.name }}</strong>
            </template>
            <template slot="action" slot-scope="{ row, index }">
              <Button type="text" size="small" @click="remove(index)">
                <img src="~/assets/delete.svg" alt="" />
              </Button>
            </template>
          </Table>
        </div>
      </Content>
    </Layout>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isCollapsed: true,
      role1: [
        {
          value: 'Admin',
          label: 'Admin',
        },
        {
          value: 'Staff',
          label: 'Staff',
        },
      ],
      show: false,
      model1: '',
      model11: '',
      loading: true,
      highestValue: '6',
      firstname: '',
      lastname: '',
      email: '',
      phone: '',
      role: 'Staff',
      value: '',
      label: '',
      columns4: [
        {
          type: 'selection',
          width: 60,
          align: 'center',
        },
        {
          title: 'FIRST NAME',
          key: 'firstname',
        },
        {
          title: 'LAST NAME',
          key: 'lastname',
        },
        {
          title: 'EMAIL',
          key: 'email',
        },
        {
          title: 'PHONE',
          key: 'phone',
        },
        {
          title: 'ROLE',
          key: 'role',
        },
        {
          title: 'Action',
          slot: 'action',
          width: 100,
          align: 'center',
        },
      ],
      data1: [
        {
          firstname: 'Joshua',
          lastname: 'Bakare',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Admin',
          value: '1',
          label: 'Joshua Bakare',
        },
        {
          firstname: 'Jane',
          lastname: 'Clement',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Staff',
          value: '2',
          label: 'Jane Clement',
        },
        {
          firstname: 'Hannah',
          lastname: 'Johnson',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Staff',
          value: '3',
          label: 'Hannah Johnson',
        },
        {
          firstname: 'John',
          lastname: 'Ngoka',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Staff',
          value: '4',
          label: 'John Ngoka',
        },
        {
          firstname: 'Omotayo',
          lastname: 'Adeleke',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Staff',
          value: '5',
          label: 'Omotayo Adeleke',
        },
        {
          firstname: 'Gloria',
          lastname: 'Amadi',
          email: 'josh.bakery@gmail.com',
          phone: '+2348012345678',
          role: 'Staff',
          value: '6',
          label: 'Gloria Amadi',
        },
      ],
    }
  },
  computed: {
    menuitemClasses() {
      return ['menu-item', this.isCollapsed ? 'collapsed-menu' : '']
    },
  },
  mounted() {
    setTimeout(() => {
      this.loading = false
    }, 1000)
  },
  methods: {
    remove(index) {
      this.data1.splice(index, 1)
    },
    generateValue() {
      this.highestValue++
    },
    onFilterSelect() {
      if (this.model1 !== '') {
        this.data1.filter((data) => {
          return data.value === this.model11
        })[0].role = this.model1
      }
    },
    createUser() {
      this.generateValue()
      this.value = this.highestValue
      this.label = `${this.firstname} ${this.lastname}`
      const user = {
        firstname: this.firstname,
        lastname: this.lastname,
        email: this.email,
        phone: this.phone,
        value: this.value,
        label: this.label,
        role: this.role,
      }
      this.data1.push(user)
      this.toggleAddEmployee()
      this.resetInputs()
    },
    resetInputs() {
      this.firstname = ''
      this.lastname = ''
      this.email = ''
      this.phone = ''
    },
    toggleAddEmployee() {
      this.show = !this.show
    },
  },
}
</script>
