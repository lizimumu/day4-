<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model.trim="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button :kk="flag" @click.prevent="add">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item, index) in arr" :key="index">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="remove(index)">删除</button>
            <button @click="edit(index, item.id)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      age: "",
      sex: "男",
      flag: true,
      arr: [],
      id: "",
    };
  },

  methods: {
    // 添加
    add() {
      const clear = () => {
        this.name = "";
        this.age = "";
        this.sex = "";
      };

      if (this.flag == true) {
        if (!this.name && !this.age) return alert("请输入学生信息");
        let obj = {
          id: this.arr.length ? this.arr.at("-1").id + 1 : 1,
          name: this.name,
          age: this.age,
          sex: this.sex,
        };
        this.arr.push(obj);
        clear();
      } else {
        console.log(66);
        let newObj = {
          id: this.id,
          name: this.name,
          age: this.age,
          sex: this.sex,
        };
        console.log(newObj);
        this.arr.forEach((item, index) => {
          console.log(item.id);
          if (item.id == this.id) {
            console.log(666);
            // this.arr[index] = newObj;
            this.arr.splice(index, 1, newObj);
            this.id = "";
            this.flag = true;
          }
        });
        console.log(this.arr);
        clear();
      }
    },
    // 删除
    remove(index) {
      this.arr.splice(index, 1);
    },
    
    edit(index, id) {
      console.log(id);
      this.name = this.arr[index].name;
      this.age = this.arr[index].age;
      this.sex = this.arr[index].sex;
      this.flag = false;
      console.log(this.flag);
      this.id = id;
      console.log(this.id);
    },
  },
};
</script>
