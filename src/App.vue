<script setup>
import { ref, computed } from "vue";
import { Input } from "@/components/ui/input";
import { Search } from "lucide-vue-next";
import {
  Table,
  TableBody,
  TableCaption,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from "@/components/ui/table";

const members = [
  {
    id: "ID1",
    fullname: "Phan Van Duc",
    position: "CEO",
    hometown: "Da Nang",
  },
  {
    id: "ID2",
    fullname: "Dang Van Lam",
    position: "Developer",
    hometown: "Da Nang",
  },
  {
    id: "ID3",
    fullname: "Bui Tien Dung",
    position: "Tester",
    hometown: "Quang Tri",
  },
  {
    id: "ID4",
    fullname: "Ho Xuan Truong",
    position: "Manager",
    hometown: "Hue",
  },
  {
    id: "ID5",
    fullname: "Leo Messi",
    position: "AM",
    hometown: "Da Nang",
  },
  {
    id: "ID6",
    fullname: "Bruno",
    position: "AM",
    hometown: "Da Nang",
  },
];

const searchTerm = ref("");

const filteredMembers = computed(() => {
  return members.filter((member) =>
    member.fullname.toLowerCase().includes(searchTerm.value.toLowerCase())
  );
});
</script>

<template>
  <div class="container flex flex-col justify-center gap-3 h-screen py-8">
    <div class="relative w-full max-w-sm items-center">
      <Input
        id="search"
        type="text"
        placeholder="Search..."
        class="pl-10"
        v-model="searchTerm"
      />
      <span
        class="absolute start-0 inset-y-0 flex items-center justify-center px-2"
      >
        <Search class="size-6 text-muted-foreground" />
      </span>
    </div>
    <Table>
      <TableCaption>A list of members.</TableCaption>
      <TableHeader>
        <TableRow>
          <TableHead class="w-[100px]"> ID </TableHead>
          <TableHead>Name</TableHead>
          <TableHead>Position</TableHead>
          <TableHead class="text-right"> Hometown </TableHead>
        </TableRow>
      </TableHeader>
      <TableBody>
        <TableRow v-for="member in filteredMembers" :key="member.id">
          <TableCell class="font-medium">
            {{ member.id }}
          </TableCell>
          <TableCell>{{ member.fullname }}</TableCell>
          <TableCell>{{ member.position }}</TableCell>
          <TableCell class="text-right">
            {{ member.hometown }}
          </TableCell>
        </TableRow>
      </TableBody>
    </Table>
  </div>
</template>
