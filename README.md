import { useState } from "react"
import { Card, CardContent } from "@/components/ui/card"
import { Input } from "@/components/ui/input"
import { Button } from "@/components/ui/button"
import { Textarea } from "@/components/ui/textarea"
import { motion } from "framer-motion"

export default function WebNovelUploader() {
  const [title, setTitle] = useState("")
  const [content, setContent] = useState("")
  const [published, setPublished] = useState(false)

  return (
    <>
      <motion.h1
        className="text-4xl font-bold mb-4 mt-6"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
      >
        ลงนิยายของกร
      </motion.h1>

      <Input
        placeholder="ชื่อเรื่อง"
        className="text-black mb-4"
        value={title}
        onChange={(e) => setTitle(e.target.value)}
      />

      <Textarea
        placeholder="เนื้อเรื่อง (ตอนนี้)"
        className="min-h-[200px] text-black mb-4"
        value={content}
        onChange={(e) => setContent(e.target.value)}
      />

      <Button
        onClick={() => setPublished(true)}
        className="w-full bg-purple-600 hover:bg-purple-700"
      >
        เผยแพร่เลย!
      </Button>

      {published && (
        <motion.div
          className="w-full max-w-xl mt-6 p-6 bg-zinc-900 rounded-2xl border border-zinc-700"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
        >
          <h2 className="text-xl font-semibold mb-2">{title || "(ไม่มีชื่อ)"}</h2>
          <p className="whitespace-pre-wrap">{content || "(ไม่มีเนื้อหา)"}</p>
        </motion.div>
      )}
    </>
  )
}
